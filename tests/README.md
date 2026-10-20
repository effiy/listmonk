---
title: listmonk E2E Tests
tags: [testing, e2e, playwright, docker, admin-ui]
category: testing
created: 2024
updated: 2026-10-20
source: external
type: index
status: stable
lifecycle: active
---

# listmonk E2E Tests

---

## 💡 概述

Playwright tests for the server-rendered admin UI. See
[Frontend tests](../docs/docs/content/developer-setup.md#frontend-tests) for the
Docker dev workflow, local prerequisites, and configuration options.

---

## ⚡ 功能

- End-to-end testing of server-rendered admin UI
- Docker-based dev environment with MailHog
- Headless and interactive UI test modes

---

## 📊 指标

「待补充」

---

## 🏛️ 设计

The suite **wipes and reinstalls the configured database schema** and stops
running listmonk processes. Use disposable data; in the Docker dev environment,
this is the `listmonk-dev` database.

Compose configures the database and existing MailHog service automatically.
Rebuild the backend after Go or SQL changes, and reinstall the browser and its
system dependencies when recreating the dev container.

---

## 📁 目录

「待补充」

---

## 🔗 资源

- [Frontend tests documentation](../docs/docs/content/developer-setup.md#frontend-tests)

---

## 🚀 快速开始

From the repository root on the host:

```sh
make build-dev-docker
make run-dev-docker
```

Inside the dev container:

```sh
make build-frontend
make build
cd tests
bun install
bun playwright install --with-deps chromium
bun run test
```

Outside Docker, install the dependencies described in the developer guide.
From `tests/`, use `bun run test` for headless tests or `bun run test:ui` for the
interactive UI.

---

## ⚙️ 技术栈

- Playwright
- Bun
- Chromium
- Docker