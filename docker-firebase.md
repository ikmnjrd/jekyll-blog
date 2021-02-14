# Firebase環境をDockerで簡単に

## dockerイメージをダウンロード
>$ docker pull andreysenov/firebase-tools


## docker-compose.ymlを作成

```
version: "3.8"
services:
  web:
    build: .
    # build:
    #   context: .
    #   dockerfile: Dockerfile
    # environment:
    #   - NODE_ENV=production
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

## test