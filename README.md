# VIT Isn't TWINT
VIT is a private initiative to create an open-source competitor to TWINT. Why we need a Twint competitor?

✅ Twint transactions are too expensives for business 1.8% + 20cts, with ViT we propose 0.3% + 1cts.<br/>
✅ To digitaly send 1 fr to a friend, you need Twint, then you need a bank account, no bank account is needed for ViT<br/>
✅ The underlying infrastructure of ViT is opensource and permissionless, that mean you can extend ViT services without asking a permission. 


Our primary objective is straightforward: acquiring all the world.

Made with ❤️ for secure and transparent blockchain payments!

# The Infrastructure
The ViT software is divided into three parts:
The **(1)** APIs [vit-core](./packages/vit-core/), **(2)** the Ethereum contracts [erc-4337](./packages/vit-erc4337-contracts/), and **(3)** the UX [vit-pay-app](./packages/vit-pay-app/).


## API 😸 (AKA. King Kong II for Web3)
The purpose of this project is to provide a simple and intuitive API for our VIT Wallet. This API facilitates spending, swapping, and lending, and is specifically designed for certain tokens such as XCHF, USDC, (BTC), and ETH (on the Optimism network).

* Account ERC-4337
* Identity
* Tx
* Core
* Config
* Tools
* DeFi

## VIT-protocol 
* todo

## VIT-UX
* todo

## Horcrux
We propose the usage of Shamir Shared Secret (SSS) to protect your Mnemonic without the problem of single point of security. We decide to use as source of SSS the entropy that produce the Mnemonic. Shamir split entropy in **N separate pieces** (called Horcruxes). Your need at least two pieces to reconstitute deterministicaly the same Mnemonic. We recomend you keep them in separate places/locations:

* Use printed paper.
* And use our Horcrux SmartContract. 👇
