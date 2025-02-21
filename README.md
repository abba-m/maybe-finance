![](https://github.com/maybe-finance/maybe/assets/35243/79d97b31-7fad-4031-9e83-5005bc1d7fd0)

# Maybe: Open-source personal finance app

<b>Get involved: [Discord](https://discord.gg/xfysSaSsfN) • [Website](https://maybe.co) • [Issues](https://github.com/maybe-finance/maybe/issues)</b>

🚨 NOTE: This is the original React/Next.js app of the now-defunct personal finance app, Maybe. This original version used many external services (Plaid, Finicity, Auth0, etc) and getting it to fully function will be a decent amount of work.

There's a LOT of work to do to get this functioning, but it should be feasible.

## Features

As a personal finance + wealth management app, Maybe has a lot of features. Here's a quick overview of some of the main ones...

-   Net worth tracking
-   Financial account syncing
-   Investment benchmarking
-   Investment portfolio allocation
-   Debt insights
-   Retirement forecasting + planning
-   Investment return simulation
-   Manual account/investment tracking

And dozens upon dozens of smaller features.

## Building the app

This is the current state of building the app. You'll hit errors, which we're working to resolve (and certainly welcome PRs to help with that).

You'll need Docker installed to run the app locally.

```
cp .env.example .env
yarn install
yarn prisma:migrate:dev
yarn prisma:seed
yarn dev
```

## High-priority issues

The biggest focus at the moment is on getting the app functional without some previously key external services (namely Auth0, Plaid and Finicity).

You can view the current [high-priority issues here](https://github.com/maybe-finance/maybe/issues?q=is:issue+is:open+label:%22high+priority%22). Those are the most impactful issues to tackle first.

## Relevant reading

-   [Learn about how the app is organized as a monorepo](https://github.com/maybe-finance/maybe/wiki/Monorepo-File-Structure-Overview)

## Credit

The original app was built by [Zach Gollwitzer](https://twitter.com/zg_dev), [Nick Arciero](https://www.narciero.com/) and [Tim Wilson](https://twitter.com/actualTimWilson), with design work by [Justin Farrugia](https://twitter.com/justinmfarrugia). The app is currently maintained by [Josh Pigford](https://twitter.com/Shpigford).

---

## ⚠️ Everything below is archived from the original repo and we're slowly working to replace/update it.

# Quick Start

## System Prerequisites

-   Docker (if not using Docker, you will need Node LTS 14.7.x and Postgres 13.x)
-   (Optional, highly recommended) - Install the [NX Console](https://marketplace.visualstudio.com/items?itemName=nrwl.angular-console) for [using the nx client](#nrwl-nx-overview)

## Run the app locally

### Setup ENV

```
cp .env.example .env
```

A working local development `.env` file can be found in 1Password under the "Engineering" folder.

### With Docker (preferred)

#### Start server and client apps

```
yarn install # re-run if it hangs
yarn dev
```

#### Migrate DB

In a separate terminal, run the following command. This will connect to the Postgres DB running inside Docker and run all the migrations in `/prisma/migrations`.

```
yarn prisma:migrate:dev
```

You will also want to seed the database (includes account types and subtypes for categorization).

```
yarn prisma:seed
```

### Manually

_NOTE: Make sure Postgres 13.x is running on your machine_

```
yarn install
nx serve client # Terminal 1
nx serve server # Terminal 2
yarn prisma:migrate && yarn prisma:seed # Terminal 3 - after apps are running
```

# Reference

## Authentication

[See this wiki page](https://github.com/maybe-finance/maybe/wiki/Auth0) for an explanation of how authentication/authorization works in this codebase.
