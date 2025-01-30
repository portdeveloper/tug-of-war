# Tap of war
A tug-of-war match where instead of pulling a rope, players are tapping buttons to move the tug to their side!

## Game Mechanics
- Players join a game using a game ID
- Each player has a "TAP!" button
- When Player 1 taps, the tug moves right (a counter is incremented in SC)
- When Player 2 taps, the tug moves left (the counter is decremented in SC)
- The game lasts 60 seconds
- Whoever has pulled the ribbon more to their side when time runs out wins

![image](https://github.com/user-attachments/assets/5d24ed5e-bebf-4462-ada2-292efa046b47)


# 🏗 Scaffold-ETH 2 - Foundry Edition + Monad Devnet configuration

<h4 align="center">
  <a href="https://docs.scaffoldeth.io">Documentation</a> |
  <a href="https://scaffoldeth.io">Website</a>
</h4>

🧪 An open-source, up-to-date toolkit for building decentralized applications (dapps) on the Ethereum blockchain. It's designed to make it easier for developers to create and deploy smart contracts and build user interfaces that interact with those contracts.

⚙️ Built using NextJS, RainbowKit, Foundry, Wagmi, Viem, and Typescript.

- ✅ **Contract Hot Reload**: Your frontend auto-adapts to your smart contract as you edit it.
- 🪝 **[Custom hooks](https://docs.scaffoldeth.io/hooks/)**: Collection of React hooks wrapper around [wagmi](https://wagmi.sh/) to simplify interactions with smart contracts with typescript autocompletion.
- 🧱 [**Components**](https://docs.scaffoldeth.io/components/): Collection of common web3 components to quickly build your frontend.
- 🔥 **Burner Wallet & Local Faucet**: Quickly test your application with a burner wallet and local faucet.
- 🔐 **Integration with Wallet Providers**: Connect to different wallet providers and interact with the Ethereum network.

![Debug Contracts tab](https://github.com/scaffold-eth/scaffold-eth-2/assets/55535804/b237af0c-5027-4849-a5c1-2e31495cccb1)

## Requirements

Before you begin, you need to install the following tools:

- [Node (>= v18.18)](https://nodejs.org/en/download/)
- Yarn ([v1](https://classic.yarnpkg.com/en/docs/install/) or [v2+](https://yarnpkg.com/getting-started/install))
- [Git](https://git-scm.com/downloads)

## Quickstart

To get started with Scaffold-ETH 2, follow the steps below:

1. Install dependencies:

```
cd my-dapp-example
yarn install

cd packages/foundry
forge install
```

2. Run a local network in the first terminal:

```
yarn chain
```

This command starts a local Ethereum network using Foundry. The network runs on your local machine and can be used for testing and development. You can customize the network configuration in `packages/foundry/foundry.toml`.

3. On a second terminal, deploy the test contract:

```
yarn deploy
```

This command deploys a test smart contract to the local network. The contract is located in `packages/foundry/contracts` and can be modified to suit your needs. The `yarn deploy` command uses the deploy script located in `packages/foundry/script` to deploy the contract to the network. You can also customize the deploy script.

4. On a third terminal, start your NextJS app:

```
yarn start
```

Visit your app on: `http://localhost:3000`. You can interact with your smart contract using the `Debug Contracts` page. You can tweak the app config in `packages/nextjs/scaffold.config.ts`.

Run smart contract test with `yarn foundry:test`

- Edit your smart contracts in `packages/foundry/contracts`
- Edit your frontend homepage at `packages/nextjs/app/page.tsx`. For guidance on [routing](https://nextjs.org/docs/app/building-your-application/routing/defining-routes) and configuring [pages/layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts) checkout the Next.js documentation.
- Edit your deployment scripts in `packages/foundry/script`

## Deploying to Monad Devnet

### Smart Contracts 

First, check out the existing `.env` file and fill in the necessary values:

```
MONAD_DEVNET_RPC_URL= 
MONAD_VERIFIER_URL=

# Do not change the name of the variable below, put monad chain id here
FOUNDRY_CHAIN_ID=
```

Also, change the `ETH_KEYSTORE_ACCOUNT` to `scaffold-eth-custom` to deploy on Monad Devnet!

Then, run the following command to deploy your contract to Monad Devnet:

```
yarn deploy --network monad_devnet
```

To verify your contract, run the following command:
```
yarn verify --network monad_devnet
```

To run both deploy and verify, run the following command:

```
yarn deploy --network monad_devnet && yarn verify --network monad_devnet
```

### Frontend

First, copy the `.env.example` file to `.env.local` and fill in the values.

Then, change the target network in `packages/nextjs/scaffold.config.ts` to `monadDevnet`

```
targetNetworks: [monadDevnet],
```

Then, run the following command to deploy your nextjs app to production:

```
yarn vercel
```

You should be able to see a URL to your app on Vercel.

## Documentation

Visit our [docs](https://docs.scaffoldeth.io) to learn how to start building with Scaffold-ETH 2.

To know more about its features, check out our [website](https://scaffoldeth.io).

## Contributing to Scaffold-ETH 2

We welcome contributions to Scaffold-ETH 2!

Please see [CONTRIBUTING.MD](https://github.com/scaffold-eth/scaffold-eth-2/blob/main/CONTRIBUTING.md) for more information and guidelines for contributing to Scaffold-ETH 2.
