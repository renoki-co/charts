- [Laravel Octane Helm Chart](#laravel-octane-helm-chart)
  - [🛑 Requirements](#-requirements)
  - [🚀 Installation](#-installation)
    - [📜 Environment variables](#-environment-variables)
    - [🤖 Run workers (non-HTTP workload)](#-run-workers-non-http-workload)
  - [📡 Monitoring](#-monitoring)
    - [❤ Healthchecks](#-healthchecks)
  - [🐛 Testing](#-testing)
  - [🤝 Contributing](#-contributing)
  - [🔒  Security](#--security)
  - [🎉 Credits](#-credits)

Laravel Octane Helm Chart
=========================

Containerize & Orchestrate your Octane-based Laravel application with this simple Helm chart.

## 🛑 Requirements

- Kubernetes v1.22+

## 🚀 Installation

To create a Laravel project image for Docker, head over to [renoki-co/laravel-helm-demo](https://github.com/renoki-co/laravel-helm-demo) to get started. The Dockerfile differs based on the project you want to deploy, and there you will find a demo application to run to understand the basics.

To install the Helm chart repository:

```bash
$ helm repo add renoki-co https://helm.renoki.org
$ helm repo update
```

Install Laravel Octane chart:

```bash
$ helm upgrade laravel-octane-app \
    --install \
    --version=1.0.0 \
    renoki-co/laravel-octane
```

Check `values.yaml` for additional available customizations.

### 📜 Environment variables

Laravel needs an `.env` file to keep secrets within, so you will need a secret from which they will be pulled. To do this, simply create a `laravel-octane-app-env` secret with the `.env` key if your helm release is called `laravel-octane-app`.

To replace the name, check for `app.envSecretName` in `values.yaml`. By default, the name is `<release name>-env`.

```yaml
kind: Secret
apiVersion: v1
metadata:
  name: laravel-octane-app-env
stringData:
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

### 🤖 Run workers (non-HTTP workload)

Workers can be for example long-lived commands, like `php artisan queue:work` commands or `php artisan horizon` that run in separate processes, other the web workers that serve HTTP content.

To deploy such workload, check the [Worker Chart](https://github.com/renoki-co/charts/tree/master/charts/laravel-worker) that will ease the job for you.

## 📡 Monitoring

### ❤ Healthchecks

For convenience, you may use [renoki-co/laravel-healthcheck](https://github.com/renoki-co/laravel-healthchecks) to easily set up healthchecks in your app, just like in `app/Http/Controllers/HealthController` presented in [renoki-co/laravel-helm-demo](https://github.com/renoki-co/laravel-helm-demo), a demo application.

In `values.yaml` you will also find a healthcheck configuration on where you can change the settings.

## 🐛 Testing

Coming soon.

## 🤝 Contributing

Please see [CONTRIBUTING](../../CONTRIBUTING.md) for details.

## 🔒  Security

If you discover any security related issues, please email alex@renoki.org instead of using the issue tracker.

## 🎉 Credits

- [Alex Renoki](https://github.com/rennokki)
- [All Contributors](../../../../contributors)
