# Building

To build our bots docker image simply run:

```typescript
docker build -t bot:v1 .
```

```typescript
2019-03-16 10:59:30 ⌚  Matthews-MacBook-Pro-178 in ~/workspace/work/discord-bot-typescript-annotationdriven
± |master S:1 U:3 ✗| → docker build -t bot:v1 .
Sending build context to Docker daemon  133.4MB
Step 1/9 : FROM node:alpine AS builder
 ---> ebbf98230a82
Step 2/9 : WORKDIR /app
 ---> Using cache
 ---> 20a4914d700a
Step 3/9 : RUN adduser -S bot
 ---> Using cache
 ---> e822599b3590
Step 4/9 : COPY package.json .
 ---> Using cache
 ---> 3b3f63ce4417
Step 5/9 : RUN npm install
 ---> Using cache
 ---> 1e9f924bcc5d
Step 6/9 : COPY . .
 ---> af99287b9757
Step 7/9 : RUN npm run build
 ---> Running in cb8b02096cef

> discord-bot-typescript-annotationdriven@1.0.0 build /app
> tsc --build tsconfig.json

Removing intermediate container cb8b02096cef
 ---> f07351e62b26
Step 8/9 : USER bot
 ---> Running in 6f96024515a5
Removing intermediate container 6f96024515a5
 ---> 9a18329f9b53
Step 9/9 : ENTRYPOINT ["npm", "start"]
 ---> Running in c65af7e9ea97
Removing intermediate container c65af7e9ea97
 ---> 51a85dcc78b6
Successfully built 51a85dcc78b6
Successfully tagged bot:v1
```

Now you can start your bot with:

```typescript
docker run --name bot -d bot:v1
```

You can view the output/logs by running:

```text
docker logs -f bot
```

