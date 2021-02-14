# Firebase環境をDockerで簡単に

## dockerイメージをダウンロード
>$ docker pull andreysenov/firebase-tools
>$ mkdir docker-firebase-test

## docker-compose.ymlを作成
commandは次の手順を実行してから追加

>$ vi docker-compose.yml

```
version: "3.8"
services:
  web:
    build: .
    volumes:
      - ./:/app 
    ports:
      - "8000:3000"
      - "4000:4000" #Emulator Suite UI
      - "5000:5000" #Firebase Hosting
      - "5001:5001" #Cloud Functions
      - "8080:8080" #Cloud Firestore
      - "8085:8085" #Cloud Pub/Sub
      - "9000:9000" #Realtime Database
      - "9005:9005" #Firebase Login
      - "9099:9099" #Authentication
    
    tty: true
    stdin_open: true
```

>$ vi Dcokerfile
```
FROM andreysenov/firebase-tools
WORKDIR /app
```

## 
>$ docker-compose up -d

コンテナに入ってreactをインストール
>$ docker exec -it docker-firebase-test_web_1 sh
>$ npx create-react-app react-ts-app --template typescript
>$ exit

## docker-compose.ymlを編集
>$ vi docker-compose.yml

```
version: "3.8"
services:
  web:
    build: .
    volumes:
      - ./:/app 
    command: sh -c "cd /app/react-ts-app && yarn start"
    ports:
      - "8000:3000"
      - "4000:4000" #Emulator Suite UI
      - "5000:5000" #Firebase Hosting
      - "5001:5001" #Cloud Functions
      - "8080:8080" #Cloud Firestore
      - "8085:8085" #Cloud Pub/Sub
      - "9000:9000" #Realtime Database
      - "9005:9005" #Firebase Login
      - "9099:9099" #Authentication
    
    tty: true
    stdin_open: true
```

>$ docker-compose up -d

## firebaseへデプロイ
>$ docker exec -it docker-firebase-test_web_1 sh
>$ cd /app/react-ts-app
>$ firebase init --localhost
>$ firebase deploy