# Spring-boot 使用 Jasypt 將 Database 重要資訊加密 

## 概述

日常工作中總會有需要將一些的敏感資訊隱藏，藉由 Jasypt 我們可以非明碼方式記載敏感資訊

例如 :

```
spring.datasource.username=root
spring.datasource.password=root
```

轉變成
```
spring.datasource.username=ENC(A9v8dup/nbF5NdX22HPNS4Q1bR7CrVcI)
spring.datasource.password=ENC(hf9v8dup/nbF5NdX22HPNS4Q1bR7CrVcI)
```

ENC() 是 Jasypt 用來辨識相關加密資訊的位置

如覺得很醜也可不使用，但就需要額外做處理，接下來，我們來看一下，他的使用方式。

## 添加套件

build.gradle 中添加如下依賴

```
implementation 'com.github.ulisesbocchio:jasypt-spring-boot-starter:3.0.5'
```

## 設置 Config

JasyptConfig

```
import org.jasypt.encryption.StringEncryptor;
import org.jasypt.encryption.pbe.PooledPBEStringEncryptor;
import org.jasypt.encryption.pbe.config.SimpleStringPBEConfig;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class JasyptConfig {

    // 自行定義的 Key，外部加/解密需要與此相同
    public static final String JASYPT_ENCRYPTOR_PWD = "bD2ogEjlJ9";

    @Bean("jasyptInfo")
    public StringEncryptor encrypt() {
        SimpleStringPBEConfig config = new SimpleStringPBEConfig();
        config.setPassword(JASYPT_ENCRYPTOR_PWD);
        config.setAlgorithm("PBEWithMD5AndDES");
        config.setPoolSize("1");

        PooledPBEStringEncryptor encryptor = new PooledPBEStringEncryptor();
        encryptor.setConfig(config);
        return encryptor;
    }
}
```

## 設置 application.properties

```
// 與設置的 Config 名稱相對應
jasypt.encryptor.bean=jasyptInfo
```

## 幫 DB 敏感資訊加密

JasyptUtil

```
import lombok.extern.slf4j.Slf4j;
import org.jasypt.encryption.StringEncryptor;
import org.jasypt.encryption.pbe.PooledPBEStringEncryptor;
import org.jasypt.encryption.pbe.config.SimpleStringPBEConfig;

@Slf4j
public class JasyptUtil {

    /**
     * @param content   enc(content)
     * @param key       
     * @param isEncrypt true(加密過的 content) -> decrypt / false(未加密的 content) -> encrypt
     */
    public static String encryptor(String content, String key, boolean isEncrypt) {
        try {
            if (content.isBlank()) {
                throw new IllegalArgumentException("Content is null");
            }

            if (key.isBlank()) {
                throw new IllegalArgumentException("Key is null");
            }

            StringEncryptor encryptor = createStringEncryptor(key);
            return isEncrypt ? encryptor.decrypt(content) : encryptor.encrypt(content);
        } catch (IllegalArgumentException i) {
            log.error(i.getMessage());
            return content;
        } catch (Exception ex) {
            log.error(ex.getMessage());
            return "Can not encrypt or decrypt this content: " + content;
        }
    }

    private static PooledPBEStringEncryptor createStringEncryptor(String key) {
        SimpleStringPBEConfig config = new SimpleStringPBEConfig();
        config.setPassword(key);
        config.setAlgorithm("PBEWithMD5AndDES");
        config.setPoolSize("1");

        PooledPBEStringEncryptor encryptor = new PooledPBEStringEncryptor();
        encryptor.setConfig(config);
        return encryptor;
    }
}
```

基本上最重要的是這段，設置完加密器後，encryptor 會將 content 依照我們所帶的 key 進行加解密

```
StringEncryptor encryptor = createStringEncryptor(key);

return isEncrypt ? encryptor.decrypt(content) : encryptor.encrypt(content);
```

舉例:

加密 - 每次 root 加密結果都會不同，但不影響解密

```
String pw = encryptor.encrypt("root",123, false)
sout(pw)

--------
d+h7vW2qjtHSuUJQorjowKSpNmWqGzpR
```

解密

```
String pw = encryptor.decrypt("d+h7vW2qjtHSuUJQorjowKSpNmWqGzpR",123, true)
sout(pw)

--------
root
```

## 參考
http://www.jasypt.org/
