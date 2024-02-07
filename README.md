# 手順

## 証明書作成

```
openssl req -x509 -newkey rsa:4096 -keyout certs\key.pem -out certs\cert.pem -nodes -days 900
```

## コンテナ起動

```
docker-compose up
```

## 公開鍵の取得

http://localhost:8080/simplesaml/saml2/idp/metadata.php?output=xhtml へアクセスし `certData` パラメーターをコピー
`certs/idp_key.pem` へ保存する

docker container の再起動

```
docker compose down && docker compose up 
```

## ブラウザで開く

### 管理者ログイン

http://localhost:8080/simplesaml/module.php/core/frontpage_welcome.php



### ログイン確認

http://localhost:3000

→ テストユーザー ID: user1 PW: user1pass で入れたらOK

※ このSAMLのユーザー情報は docker container へ attach して /var/www/simplesamlphp/config/authsources.php にあり。