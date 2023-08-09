# Enabling a Network

### In the website repository

1. Go to the chain definition file

{% embed url="https://github.com/tradescrow/website/blob/develop/src/data/chains.ts" %}

2. Find the chain in question and
   * Update `usdc` to the USDC token address
   * Update `tradescrow` to the chain-specific address
   * Update `graphId` to the string name of the chain as defined in the [supported network page of TheGraph](https://thegraph.com/docs/en/developing/supported-networks/)
   * Add a dex record definition with a name and a url like:\
     `dex: {`\
     &#x20; `name: "Trader Joe",`\
     &#x20; `url: "https://traderjoexyz.com/avalanche/trade"`\
     `},`
   * add `enabled: true,`

### In the thegraph repository

1. Get the chain definition from the supported network page of TheGraph

{% embed url="https://thegraph.com/docs/en/developing/supported-networks/" %}

2. Go to the networks json file and add the new network definition\
   Network definition synax:

```json
"{CLI Name from thegraph}": {
  "Tradescrow": {
    "address": "0xasdfasdfasdf", // tradescrow contract address
    "startBlock": 12345 // blockNumber the contract was deployed
  }
} 
```

{% embed url="https://github.com/tradescrow/thegraph/blob/main/networks.json" %}

{% hint style="info" %}
You can obtain the block number by going to the contract address on the chain's block explorer, clicking the transaction hash, and copying the block number
{% endhint %}

3. Edit the package.json file, adding the new network definition in scripts. \
   Script definition syntax:

```sh
"deploy:{chainName}": "graph deploy --node https://api.studio.thegraph.com/deploy/ --network={chainName} --version-label={last release} tradescrow-{chainName}",
```

4. Check the dashboard to make sure it syncs to 100% at `https://thegraph.com/studio/subgraph/tradescrow-{chainName}/`
