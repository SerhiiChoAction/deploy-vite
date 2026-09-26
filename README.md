# Secure Copy Files with SSH

Forgejo composite action to build and rsync your Vite project to a destination server.

## Runner Requirements

Here are the packages that needs to be installed on runner:

- bash
- rsync

## Usage Example

```yml
name: Deploy
enable-email-notifications: true

on:
  push:
    branches: [master]

jobs:
  deploy:
    name: Deploy Vite App
    runs-on: debian13-podman

    steps:
      - name: Install deps
        run: apt update && apt install -y rsync

      - name: Checkout
        uses: actions/checkout@v6

      - name: Deploy Vite App
        uses: https://codeberg.org/act/vite-deploy@v1
        with:
          host-user: ${{ secrets.HOST_USER }}
          host-ip: ${{ secrets.HOST_IP }}
          host-key: ${{ secrets.HOST_SSH_PRIVATE_KEY }}
          from: dist/
          to: ~/my-project
```
