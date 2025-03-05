## Blockscout

Blockscout allows users to search transactions, view accounts and balances, verify and interact with smart contracts and view and interact with applications on the Ethereum network including many forks, sidechains, L2s and testnets.

Blockscout is an open-source alternative to centralized, closed source block explorers such as Etherscan, Etherchain and others.  As Ethereum sidechains and L2s continue to proliferate in both private and public settings, transparent, open-source tools are needed to analyze and validate all transactions.

## Getting Started

See the [project documentation](https://docs.blockscout.com/) for instructions:

- [Docker-compose deployment](https://docs.blockscout.com/for-developers/deployment/docker-compose-deployment)
- [ENV variables](https://docs.blockscout.com/setup/env-variables)
- [Configuration options](https://docs.blockscout.com/for-developers/configuration-options)

## Prerequisites

- Docker v20.10+
- Docker-compose 2.x.x+
- Running Ethereum JSON RPC client

## Building Docker containers from source

```bash
cd ./docker-compose
docker-compose up --build
```

> Note: you can use docker compose instead of docker-compose, if compose v2 plugin is installed in Docker.