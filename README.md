# Deploy Vite App

Composite action to build and rsync your Vite project to a destination server.

## Runner Requirements

Here are the packages that needs to be installed on runner:

- bash
- rsync
- npm

## Usage Example

```yml
name: Deploy Vite App

on:
  push:
    branches: [master]

jobs:
  deploy:
    name: Deploy Vite App
    runs-on: ubuntu-latest

    steps:
      - name: Install deps
        run: apt update && apt install -y rsync

      - name: Checkout
        uses: actions/checkout@v6

      - name: Deploy Vite App
        uses: SerhiiChoAction/deploy-vite@v1
        with:
          host-user: ${{ secrets.HOST_USER }}
          host-ip: ${{ secrets.HOST_IP }}
          host-key: ${{ secrets.HOST_SSH_PRIVATE_KEY }}
          from: dist/
          to: ~/my-project
          pages-branch: my-project.github.io
```
