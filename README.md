## fly.io Remote Deployment

Official documentation: https://fly.io/docs/

Use Docker image to deploy fly.io application

```bash
flyctl launch --image yym68686/chatgpt:latest
```

Enter the name of the application when prompted, and select No for initializing Postgresql or Redis.

Follow the prompts to deploy. A secondary domain name will be provided in the official control panel, which can be used to access the service.

Set environment variables

```bash
flyctl secrets set BOT_TOKEN=bottoken
flyctl secrets set API=
# optional
flyctl secrets set WEB_HOOK=https://flyio-app-name.fly.dev/
flyctl secrets set NICK=javis
```

View all environment variables

```bash
flyctl secrets list
```

Remove environment variables

```bash
flyctl secrets unset MY_SECRET DATABASE_URL
```

ssh to fly.io container

```bash
flyctl ssh issue --agent
# ssh connection
flyctl ssh establish
```

Check whether the webhook URL is correct

```bash
https://api.telegram.org/bot<token>/getWebhookInfo
```

## Docker Local Deployment

Start the container

```bash
docker run -p 80:8080 --name chatbot -dit \
    -e BOT_TOKEN=your_telegram_bot_token \
    -e API= \
    -e API_URL= \
    -v ./user_configs:/home/user_configs \
    yym68686/chatgpt:latest
```