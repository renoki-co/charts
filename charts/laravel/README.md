Laravel Helm Chart
==================

Containerize & Orchestrate your Laravel application with this simple Helm chart.

## 🤝 Supporting

Renoki Co. on GitHub aims on bringing a lot of open source projects and helpful projects to the world. Developing and maintaining projects everyday is a harsh work and tho, we love it.

If you are using your application in your day-to-day job, on presentation demos, hobby projects or even school projects, spread some kind words about our work or sponsor our work. Kind words will touch our chakras and vibe, while the sponsorships will keep the open source projects alive.

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/R6R42U8CL)

## 🚀 Installation

To create a Laravel project image for Docker, head over to [renoki-co/laravel-helm-demo](https://github.com/renoki-co/laravel-helm-demo) to get started.

```bash
$ helm repo add renoki-co https://helm.renoki-co.org
$ helm repo update
```

## 🙌 Usage

Some info.

# Environment

Laravel needs an `.env` file to keep secrets within, so you will need a secret from which they will be pulled. To do this, simply create a `laravel-env` secret with the `.env` key.

To replace the name, check for `app.envSecretName` in `values.yaml`.

```yaml
kind: Secret
apiVersion: v1
metadata:
  name: laravel-env
data:
  .env: |
    APP_NAME=Laravel
    APP_ENV=production
    APP_KEY=base64:kLHmdtqS0YnTACWSpkV4w1GVOQMEXQ68Usk8WR+yauA=
    APP_DEBUG=true
    APP_URL=http://test.laravel.com

    LOG_CHANNEL=null
    LOG_LEVEL=debug

    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=laravel
    DB_USERNAME=root
    DB_PASSWORD=

    BROADCAST_DRIVER=log
    CACHE_DRIVER=file
    QUEUE_CONNECTION=sync
    SESSION_DRIVER=file
    SESSION_LIFETIME=120

    MEMCACHED_HOST=127.0.0.1

    REDIS_HOST=127.0.0.1
    REDIS_PASSWORD=null
    REDIS_PORT=6379

    MAIL_MAILER=smtp
    MAIL_HOST=mailhog
    MAIL_PORT=1025
    MAIL_USERNAME=null
    MAIL_PASSWORD=null
    MAIL_ENCRYPTION=null
    MAIL_FROM_ADDRESS=null
    MAIL_FROM_NAME="${APP_NAME}"

    AWS_ACCESS_KEY_ID=
    AWS_SECRET_ACCESS_KEY=
    AWS_DEFAULT_REGION=us-east-1
    AWS_BUCKET=

    PUSHER_APP_ID=
    PUSHER_APP_KEY=
    PUSHER_APP_SECRET=
    PUSHER_APP_CLUSTER=mt1

    MIX_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
    MIX_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"
```

## 🐛 Testing

Some info.

## 🤝 Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## 🔒  Security

If you discover any security related issues, please email alex@renoki.org instead of using the issue tracker.

## 🎉 Credits

- [Alex Renoki](https://github.com/rennokki)
- [All Contributors](../../contributors)
