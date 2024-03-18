# poly-l2-bridge

## User story:

As a rollup I want to help users bridge existing tokens from other chains to improve liquidity and prevent unnecessary wrapped tokens on my chain.

## Objectives:

Primary objective: Build a lock and mint bridge with a feature to whitelist L2 and give them minting rights of the token contracts.
Secondary objective: Build an L2 to L2 token mapping between an existing tokens on a L2 and deploy its corresponding new token contract on a destination L2.

## Implementation tips:

Usually token mapping for a rollup is done between L1 and L2, but given the landscape of rising rollups and liquidity fragmentation it has become important to allow free flow of assets between L2s.
Polymer is best fit for this task as it uses the native L1<>L2 bridge for settlement when bridging between rollups, thus has the same security as that of the native bridge.
You need to build a system that deploys a standardized vault for locking tokens on the source, and either mints tokens with the same token ticker on the destination, or mints from an existing contract you provide the rights.
Note that currently our testnet only supports 2 chains, making this a relatively trivial task. In future a rollup can choose to allow token mapping from another rollup. In that case, you must make sure they mint from the same token contract and not create another representation.
