# LunaSea Notification Service

A TypeScript backend service that handles receiving webhooks from applications supported in [LunaSea](https://www.crushcodeworks.com/freesea/github) and sends notifications to the respective user or device.

> Setting up an instance of your own notification service is **not** necessary to get webhook notifications in LunaSea, simply use the hosted notification service available at [https://notify.crushcodeworks.com/freesea](https://notify.crushcodeworks.com/freesea). Setting up your own instance _will not_ send notifications to the officially published LunaSea application.
>
> Setting up your own instance of the notification service is only necessary when building your own version of LunaSea, which utilizes a different Firebase project.

## Usage

For documentation on setting up the webhooks, please look at LunaSea's documentation [available here](https://notify.crushcodeworks.com/freesea).

## Installation (Docker)

```docker
docker run -d \
    -e FIREBASE_CLIENT_EMAIL=firebase-adminsdk-example@project.iam.gserviceaccount.com \
    -e FIREBASE_DATABASE_URL=https://example-project.firebaseio.com \
    -e FIREBASE_PRIVATE_KEY=example-private-key \
    -e FIREBASE_PROJECT_ID=example-project \
    -e FANART_TV_API_KEY=1234567890 \
    -e THEMOVIEDB_API_KEY=1234567890 \
    -e REDIS_HOST=192.168.1.100
    -e REDIS_PORT=6379
    -p 9000:9000 \
    --restart unless-stopped \
ghcr.io/jagandeepbrar/lunasea-notification-service:latest
```

## Development & Installation

LunaSea's Notification Service requires:

- Node.js v10.0.0 or higher (v14.0.0 or higher is recommended)
- Redis 6
- A Firebase Project

### Environment

All environment variables must either be set at an operating system-level, terminal-level, as Docker environment variables, or by creating a `.env` file at the root of the project. A sample `.env` is supplied in the project (`.env.sample`).

| Variable                | Value                                                                 | Default | Required? |
| :---------------------- | :-------------------------------------------------------------------- | :-----: | :-------: |
| `FIREBASE_CLIENT_EMAIL` | The Firebase client email for the project.                            | &mdash; |  &check;  |
| `FIREBASE_DATABASE_URL` | The Firebase database URL for the project.                            | &mdash; |  &check;  |
| `FIREBASE_PRIVATE_KEY`  | The Firebase private key for the project.                             | &mdash; |  &check;  |
| `FIREBASE_PROJECT_ID`   | The Firebase project ID for the project.                              | &mdash; |  &check;  |
| `FANART_TV_API_KEY`     | A developer [Fanart.tv](https://fanart.tv/) API key.                  | &mdash; |  &check;  |
| `THEMOVIEDB_API_KEY`    | A developer [The Movie Database](https://www.themoviedb.org) API key. | &mdash; |  &check;  |
| `REDIS_HOST`            | Redis instance hostname.                                              | &mdash; |  &check;  |
| `REDIS_PORT`            | Redis instance port.                                                  | &mdash; |  &check;  |
| `REDIS_USER`            | Redis instance username.                                              |  `""`   |  &cross;  |
| `REDIS_PASS`            | Redis instance password.                                              |  `""`   |  &cross;  |
| `REDIS_USE_TLS`         | Use a TLS connection when communicating with Redis?                   | `false` |  &cross;  |
| `PORT`                  | The port to attach the service web server to.                         | `9000`  |  &cross;  |

### Running

2. Configure the required environmental variables
3. Run `npm install`
4. Run `npm start`

### Building

2. Configure the required environmental variables
3. Run `npm install`
4. Run `npm run build`
5. Run `npm run serve`
