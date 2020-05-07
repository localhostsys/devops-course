# Build locally
`docker build -t my-probot .`

# Test the project
`docker run -it --rm my-probot npm run test`

# Test out running locally

This starts things up locally without connecting to a GitHub App.

```
docker run  -it --rm \
            -e NODE_ENV=dev \
            -e APP_ID=aaa \
            -e WEBHOOK_SECRET=bbb \
            -e PRIVATE_KEY=$(echo abcd|base64) \
            -p 3000:3000 my-probot npm start
```

Try opening a browser to http://localhost:3000 to see the probot web start.

# Develop locally

Changes to your source code get reflected in the container and node restarts
our app with the latest changes.

```
docker run  -it --rm \
            -e APP_ID=abc \
            -e PRIVATE_KEY=none \
            -w /home/node/my-probot-dev \
            -v "$(pwd)":/home/node/my-probot-dev \
            -p 3000:3000 my-probot \
            bash -c 'npm install && npm run dev'
```

# Lint Test
`docker run -it --rm my-probot npm run lint`

# Show Coverage Report
`docker run -it --rm my-probot npm run coverage`
