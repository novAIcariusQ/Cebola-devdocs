---
title: Installation and run
nav_order: 2
---

# Installation and run
{: .no_toc }

## Table Of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

{: .warning}
> This page may require some additional info about backend and might not be fully covered, cause all of it's current content was based on [Fronted README.md](https://github.com/novAIcariusQ/Cebola-Frontend).

## Stack

- React 18
- Vite
- TypeScript
- Tailwind CSS
- React Router
- Axios with baseURL: /api
- i18next + react-i18next
- lucide-react icons


## To do it manually

### Requirements

- Node.js 20+ recommended
- npm

The project was last checked with Node `24.14.1`.

### Installation

Clone the repo and cd into project:
```bash
git clone https://github.com/novAIcariusQ/Cebola-Frontend.git
cd Cebola-Frontend
```

Install:
```bash
npm install
```

If npm optional dependencies break on Windows, clean the install and run it again:
```bash
Remove-Item -Recurse -Force node_modules, package-lock.json
npm install
```

### Run

```bash
npm run dev
```

Default local URL is `http://localhost:3000`

Vite proxies /api to `http://localhost:3001`

The proxy is configured in vite.config.ts.

### Build

```bash
npm run build
```

This runs TypeScript checks and then `vite build`.


## To do it via docker

### Requirements

- docker
- docker-compose

{: .note}
> You may also need to add your user to docker group and reboot your pc. You can follow for exmple [this guide](https://dev.to/abhay_yt_52a8e72b213be229/how-to-install-docker-on-windows-macos-and-linux-a-step-by-step-guide-3a2i) to install Docker on your system.

### Run

Clone the repo and cd into project:
```bash
git clone https://github.com/novAIcariusQ/Cebola-Frontend.git
cd Cebola-Frontend
```

Run:
```bash
docker compose up
```

### Build

```bash
docker build . -t cebola-frontend
```

## Demo Access

Backend auth is not required for merchant frontend development. Open `/login/sign-in` and click Use local demo access; this stores a local frontend token and redirects to /merchant/shops.

The customer storefront is public and starts at /. It can use backend public endpoints or local demo data derived from merchant demo storage.
