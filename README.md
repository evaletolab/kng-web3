# VIT Isn't TWINT
VIT is a private initiative to create an open-source competitor to TWINT. 
Our primary objective is straightforward: acquiring all the world.

## kng2-web3 😸 (AKA. King Kong II for Web3)
The purpose of this project is to provide a simple and intuitive API for our VIT Wallet. This API facilitates spending, swapping, and lending, and is specifically designed for certain tokens such as XCHF, USDC, (BTC), and ETH (on the Optimism network).

But the main feature provides a solid solution to protect you **Digital Identity**.

## APIs (checked for v0.01)
### config.option
* [ ] `aavePoolProviderAddress`
* [ ] `aavePoolProviderABI`
* [ ] `aaveContractAddress`
* [ ] `aaveTokenAddress`
* [ ] `rocketPoolContractAddress`
* [ ] `uniswapRouterAddress` 
* [ ] `USDC_CONTRACT_ADDRESS`
* [ ] `RPL_CONTRACT_ADDRESS`
* [x] `XCHF_CONTRACT_ADDRESS`
* [x] `salt`
* [x] `allowedTokens`
* [x] `networks`

### Tools
- [x] `tools.config`: Secure configuration for the project.
- [x] `tools`: Utilities (Secure Session Storage , Converters, ...).

### Core
- [x] `core.identity`: Manage and secure an identity associated with the device (**DOING**)
- [x] `core.AES`: Simple AES encryption wrapper available natively on the browser.
- [x] `core.POW`: Simple Proof-of-Work API.
- [x] `core.SSS`: Shamir's Secret Sharing Wrapper.
- [x] `core.XOR`: Shuffle operations to avoid clear content.
- [x] `core.entropy`: API related to Mnemonics and seed.
- [x] `core.derivation`: API related to key derivation.

### Tx
- [x] `evm.transaction`: Interact with the ETH network to sign/send/read/list transactions (**TODO**).
- [ ] `btc.transaction`: Interact with the BTC network to sign/send/read/list transactions (**TODO**).
- [x] `transaction`: high level api for transactions that include  black/white-addresses.
- [x] `paymaster`: paymasters allow users to sponsor transactions or accept  **xCHF** (ERC20 tokens) for gas payment (**TODO**).

### DeFi
- [ ] `defi.aave`: Interact with the Aave protocol to lend USDC.
- [ ] `defi.rocketpool`: Interact with the Rocket Pool to stake ETH.
- [ ] `defi.uniswap`: Interact with Uniswap to swap XCHF <=> USDC.

### Others
- [ ] Use [scam-database/blacklist](https://github.com/scamsniffer/scam-database/tree/main/blacklist) (**TODO**)


## Digital Identity
Digital identity is a new reality, it appears complex or wird because we have no practice on that subject. The goal of VIT is to provide a few solutions to protect your identiy without the needs of a trusted thirdparties.

A Digital Identity is simply a 32-bytes large number, often represented as a mnemonic of 12/15/24 words (to facilitate human memorization of words instead of numbers). With this large number, you are able to generate an infinite number of Wallets and public identities.

Okay, but what it means for a day-to-day life? With this **secret large number**, you can generate multiple digital identities: one for cash transactions, one to collect funds for a birthday, some for social networks, some are publics, some are privates.

To achieve that goal, we built a simple and deterministic API as a frictionless solution to manage your own private mnemonic.

## Use Horcruxes/SSS to recover your identity
To increase the security of your identity, we break the Mnemonic phrase (**the secret large number**) into 3 separate pieces (called Horcruxes). You need at **least two pieces** to reconstitute your identity. You decide where you want to store each Horcrux. We recommend you keep them in separate places/locations. We provide a few alternatives (do not keep all of them on trusted third parties):

* One Horcrux is stored on the device.
* One or two Horcruxes are stored on printed paper and kept in separate places/locations.
* One is stored on our Vault SmartContract, a digital and secure place.


## Preparing content
Before storing Horcruxes on your devices or on public ledgers, we use our API to protect the content.

* **Secret-Leafs (A/B)** are generated client-side with the preimage of a pseudo, password, and POW. 
* The POW element is the [puzzle](https://en.wikipedia.org/wiki/Proof_of_work#List_of_proof-of-work_functions) result of user sha256(username, password). It's a simple way to protect against DoS attacks. 
* Users can also choose to store the pseudo/password form fields on a third-party service.
* **Public-Leafs (A/B)** are derivated images of **Secret-Leafs (A/B)**, These values can be used for specific **online** features, such as storing a Horcrux in a public blockchain.
* **Public-Leaf0** is the result of sha256(leaf1, leaf2). This publicKey (leaf0) will be used as address to store a Horcrux.


[![](https://mermaid.ink/img/pako:eNqdl1tv4jgUgP9KlNFIHS2g3C99K9BKK1W7D2X3ZZgHJ3bAwiSs40zLlv73sXMptkMCu46EEp_vXHxsH5t3My0gMu_NDQWHrbFarnODt7JKmo5DlRCcTgkCWdmI_vp9-V18WtOSFRTBaYXhD2M6nRon0W2fWp2HT_wsdDrhvBGiHDYvrcqZdE9GiVKK2IMMzM-A1wGtKS3uRibH3ZozprOp8dDvmstd87pr0e_i6dEi7zpGPDcOTuUWnIyqRDQHe3T3Xbz9-NYQc4k4FK92I_2Nv3ZE7e_GkS5Va05nDZSlbHJxIawaei0olHS0EMRjTsw9onuAIV8570K8NtkW7dHavOevEGWgImxtTiTR34BikBBUCua9HYqZgHS3oUXFbdeqr1vMUKso5AeK94AeFwUpaEN8eVw8Lp6eJIZnoMihRmW8QdkSQ5RhFdqW5C6yJoZtWV8nRhzMnNDzrTiy3Pjrt34Qc54XRDV9x-MGAqEfDep_BnjRQvBpwJ35TuzZdhh4oWKgi_2ifnQ9gHYAK_TG5BzZru1a1qVAddLizbEvRKSBdJPcxTPfapvNszr4JQdIcI5kf27dFH9qQKqUr8R8vtuML5Az0FsbSZ1XuxXHbmgt5z2x04oBb4p3QGnxukUAjo4gK3L2BPaYHBtiveajoiip0i1ixr4U3xPjJ6IQ5GBiiN1CNPUX_G-7w-zg8CanDySIzLWt9AVF4pGwnJf6kTTV4nqoQ4lISVXymR_JZEfIZnoJa-vDM85345OOGUHDs47gBj3fNnKQ8rNKDqreun48C5zADiLH8dyJwT_DMPDdwLWdSOyncBZbdhxYYeS5yn5qzA1nspZrWyMhPEqdeVbX_Yaio7xu8SYHZDgBjXw1ujWapVG88WhHi-gnd7HI_e9M1WavZIIUxeEKkhcM9SLrL6waUwfKF6gPoMZcnxr8EzBc5H2fQRBcJjW3nniUGvRPhfIU_VHtE8WifuLxYtW3x-squLMtR5xV_Mfx_YlhzbxYWZSEvVzSveLAOSfKUw4DBspdf_y-62VJqmPq4CMQWxBqjMj5M95s2UhoHXcDsgR0NzKFHfZnxUoM0Q3kgt8vd-KCop57rh24-oSj1W2pkWA1QUmWhlkmkRuK5dODiDxpxQAW-QVTo6QeocalFLP-KLIs4k3H1NWIlMktIDhqhUwl6iIwMgWIH6BUS5HvO7zpkF7relRK-I1VUENXnAwTsjoekDVUCDvAHjriOsA510fX8q7fIjs996xnO2e9wctfp-dJemFwuz__rDf9D-4C6YZ5u7NQCjKKBr0JtY91_sH_SFQHCBh6hJgfh-Z9BkiJJiaoWPFyzFPzntEKddASA_6fZ99SH78A4ZdVLg)](https://mermaid-js.github.io/mermaid-live-editor/edit/#pako:eNqdl1tv4jgUgP9KlNFIHS2g3C99K9BKK1W7D2X3ZZgHJ3bAwiSs40zLlv73sXMptkMCu46EEp_vXHxsH5t3My0gMu_NDQWHrbFarnODt7JKmo5DlRCcTgkCWdmI_vp9-V18WtOSFRTBaYXhD2M6nRon0W2fWp2HT_wsdDrhvBGiHDYvrcqZdE9GiVKK2IMMzM-A1wGtKS3uRibH3ZozprOp8dDvmstd87pr0e_i6dEi7zpGPDcOTuUWnIyqRDQHe3T3Xbz9-NYQc4k4FK92I_2Nv3ZE7e_GkS5Va05nDZSlbHJxIawaei0olHS0EMRjTsw9onuAIV8570K8NtkW7dHavOevEGWgImxtTiTR34BikBBUCua9HYqZgHS3oUXFbdeqr1vMUKso5AeK94AeFwUpaEN8eVw8Lp6eJIZnoMihRmW8QdkSQ5RhFdqW5C6yJoZtWV8nRhzMnNDzrTiy3Pjrt34Qc54XRDV9x-MGAqEfDep_BnjRQvBpwJ35TuzZdhh4oWKgi_2ifnQ9gHYAK_TG5BzZru1a1qVAddLizbEvRKSBdJPcxTPfapvNszr4JQdIcI5kf27dFH9qQKqUr8R8vtuML5Az0FsbSZ1XuxXHbmgt5z2x04oBb4p3QGnxukUAjo4gK3L2BPaYHBtiveajoiip0i1ixr4U3xPjJ6IQ5GBiiN1CNPUX_G-7w-zg8CanDySIzLWt9AVF4pGwnJf6kTTV4nqoQ4lISVXymR_JZEfIZnoJa-vDM85345OOGUHDs47gBj3fNnKQ8rNKDqreun48C5zADiLH8dyJwT_DMPDdwLWdSOyncBZbdhxYYeS5yn5qzA1nspZrWyMhPEqdeVbX_Yaio7xu8SYHZDgBjXw1ujWapVG88WhHi-gnd7HI_e9M1WavZIIUxeEKkhcM9SLrL6waUwfKF6gPoMZcnxr8EzBc5H2fQRBcJjW3nniUGvRPhfIU_VHtE8WifuLxYtW3x-squLMtR5xV_Mfx_YlhzbxYWZSEvVzSveLAOSfKUw4DBspdf_y-62VJqmPq4CMQWxBqjMj5M95s2UhoHXcDsgR0NzKFHfZnxUoM0Q3kgt8vd-KCop57rh24-oSj1W2pkWA1QUmWhlkmkRuK5dODiDxpxQAW-QVTo6QeocalFLP-KLIs4k3H1NWIlMktIDhqhUwl6iIwMgWIH6BUS5HvO7zpkF7relRK-I1VUENXnAwTsjoekDVUCDvAHjriOsA510fX8q7fIjs996xnO2e9wctfp-dJemFwuz__rDf9D-4C6YZ5u7NQCjKKBr0JtY91_sH_SFQHCBh6hJgfh-Z9BkiJJiaoWPFyzFPzntEKddASA_6fZ99SH78A4ZdVLg)

This how identity is used to prepare Horcruxes of our Identity.


[![](https://mermaid.ink/img/pako:eNqdV1uP4jYU_itR0EpMl2FyJyDtSp2bKnXUrcSofVj2wUkcsAgJdZyZoaP573ucC7EdEmiNROSc79w-Hx8773qYRVhf6DlDDN8TtKZod_1irVINxvdffmjX11-15XJ5k2oLbblBO0K1JQ4pZnxG8U26SitwaUHbZDSkxds4LzGTPM9v0ivtXVNGpcJHZZt72ZE3TFtBZaGVLDRUsM34SvvytZaNBDMlpATXEYDRSvpRPdrXHJSzjOIm8jSDwClZb5iWxZUIkuVPtMbf90XwOz780L5oBUmZ5Xrjo6mrlZJ9GWGRY5qiHZ7sUZ6_ZjQazL_huNECzyTCKSPscLRU5lyQqKvVuBC1WregtRe1jj5KCioOW-nR1klpQ3kp3KBRNV8ImbRvSxCECBXz2691KYyqcIogIeFxYUTupKwvpkysgWrOJX9--3vEZ6dkPExZ1qAl8UIzDcPY5RoEnb3Cv8tncrZHpWOu_M1nwDcrdnPk_6OqFX2i7zDdIRLBpnvnopXONniHVzpwqUc4RkXCVvpEEP2FKEFBgnOOea_MrfQAhds1zYo0qlRfN4ThWpHL95TsED3cZUlGK8To4e7h7vFRwMDSZGmkoGIYkWiJYcqIDNrkydg3JpyjTxNt7k2tmeMac9-w55-uukHcQllhquhbDhjwuL7fq38M8KQF72jAnrrW3DHNmefMJANN7Cf1_fMB1Ak84zcmcmTapm0YpwJVkVBEhmWeiEgB0nUwnk9dox4msNo7EwNMSIpFf3Y5JH9yQLIUKjG93a6HC6QFdGojKHk1a_Hcnhn3tx2xVYsRDMk7ojR73WAUDWYQZyl7hJMnOVSI1Qqyojgowg30GtiUMJ9oL5hGKEUTje-WRFFfkn_rHWZ6-zeRPhTg5FbZSiPs858AS-GUHKCpFJep9hERJkUOKz_AZIMQzXQIq_vDE0m3w4tOWIL7Vx1Ha_x0WeYohHNQDKrcuu586lme6fmW5dgTDaazmefanm1aPt9Ps-ncMOeeMfMdW9pPlbl-Jku5sjWCBKJUMU9y3a8pPoh1S9YpSvoJqOTPg1ujKo3sDaIdbKJH3Mkm97-ZKs2eYSLJsv0ZCL_cdCLrFlYJkxOFAnVRpGDOLw15QYxkaden53mnkYpbh_-kHvRPgdMQ_1HsAsmieuJBs-rag76KxqZh8bMK_izXnWjG1JlLRZmw5SndMw6slihHOgwYyrfd_F3biYNQhcnJ-2huRJGC4Zw_8evpQGgN7gLIPaLbgSVsYN8KlsOd7ALkHVzptvyCIp97tunZ6oLj58uoEcAyQUEczuJYQK4pEU-PhPOkNIMoS0-YGkSqESq4kBLWzSKOfRgqTK5GLC1uFqGD0shkRNkEBpYAwwFKFYpc14KhgtRe10GFCdz_OarvihOTJHk-7LHR1wgbgNl3xDUAq-2PtuGcv0U2enarZ1qtXu_lr9FzBL2Zd7k_t9W7_g_uPOGGebmzmRCk7_d642rwLfEBHxLFPoIPp4eIwHGoL2KU5Hiiwydotjykob5gtMANqP6yr1EfPwGx6qMs)](https://mermaid-js.github.io/mermaid-live-editor/edit/#pako:eNqdV1uP4jYU_itR0EpMl2FyJyDtSp2bKnXUrcSofVj2wUkcsAgJdZyZoaP573ucC7EdEmiNROSc79w-Hx8773qYRVhf6DlDDN8TtKZod_1irVINxvdffmjX11-15XJ5k2oLbblBO0K1JQ4pZnxG8U26SitwaUHbZDSkxds4LzGTPM9v0ivtXVNGpcJHZZt72ZE3TFtBZaGVLDRUsM34SvvytZaNBDMlpATXEYDRSvpRPdrXHJSzjOIm8jSDwClZb5iWxZUIkuVPtMbf90XwOz780L5oBUmZ5Xrjo6mrlZJ9GWGRY5qiHZ7sUZ6_ZjQazL_huNECzyTCKSPscLRU5lyQqKvVuBC1WregtRe1jj5KCioOW-nR1klpQ3kp3KBRNV8ImbRvSxCECBXz2691KYyqcIogIeFxYUTupKwvpkysgWrOJX9--3vEZ6dkPExZ1qAl8UIzDcPY5RoEnb3Cv8tncrZHpWOu_M1nwDcrdnPk_6OqFX2i7zDdIRLBpnvnopXONniHVzpwqUc4RkXCVvpEEP2FKEFBgnOOea_MrfQAhds1zYo0qlRfN4ThWpHL95TsED3cZUlGK8To4e7h7vFRwMDSZGmkoGIYkWiJYcqIDNrkydg3JpyjTxNt7k2tmeMac9-w55-uukHcQllhquhbDhjwuL7fq38M8KQF72jAnrrW3DHNmefMJANN7Cf1_fMB1Ak84zcmcmTapm0YpwJVkVBEhmWeiEgB0nUwnk9dox4msNo7EwNMSIpFf3Y5JH9yQLIUKjG93a6HC6QFdGojKHk1a_Hcnhn3tx2xVYsRDMk7ojR73WAUDWYQZyl7hJMnOVSI1Qqyojgowg30GtiUMJ9oL5hGKEUTje-WRFFfkn_rHWZ6-zeRPhTg5FbZSiPs858AS-GUHKCpFJep9hERJkUOKz_AZIMQzXQIq_vDE0m3w4tOWIL7Vx1Ha_x0WeYohHNQDKrcuu586lme6fmW5dgTDaazmefanm1aPt9Ps-ncMOeeMfMdW9pPlbl-Jku5sjWCBKJUMU9y3a8pPoh1S9YpSvoJqOTPg1ujKo3sDaIdbKJH3Mkm97-ZKs2eYSLJsv0ZCL_cdCLrFlYJkxOFAnVRpGDOLw15QYxkaden53mnkYpbh_-kHvRPgdMQ_1HsAsmieuJBs-rag76KxqZh8bMK_izXnWjG1JlLRZmw5SndMw6slihHOgwYyrfd_F3biYNQhcnJ-2huRJGC4Zw_8evpQGgN7gLIPaLbgSVsYN8KlsOd7ALkHVzptvyCIp97tunZ6oLj58uoEcAyQUEczuJYQK4pEU-PhPOkNIMoS0-YGkSqESq4kBLWzSKOfRgqTK5GLC1uFqGD0shkRNkEBpYAwwFKFYpc14KhgtRe10GFCdz_OarvihOTJHk-7LHR1wgbgNl3xDUAq-2PtuGcv0U2enarZ1qtXu_lr9FzBL2Zd7k_t9W7_g_uPOGGebmzmRCk7_d642rwLfEBHxLFPoIPp4eIwHGoL2KU5Hiiwydotjykob5gtMANqP6yr1EfPwGx6qMs)

## Horcrux
We propose the usage of Shamir Shared Secret (SSS) to protect your Mnemonic without the problem of single point of security. We decide to use as source of SSS the entropy that produce the Mnemonic. Shamir split entropy in **3 separate pieces** (called Horcruxes). Your need at least two pieces to reconstitute deterministicaly the same Mnemonic. We recomend you keep them in separate places/locations:

* Use printed paper.
* And use our Horcrux SmartContract. 👇
[![](https://mermaid.ink/img/pako:eNqdV-mO2zYQfhVBQQBv61V1SzaQBboXFsii-bFGESAOCkoa2ax1OBS1u84iL5VH6JN1dNkSZcluacAQNd9cH4dD6k320wDkuZxxwuGWkhUj8eWzvkyWiYRjnTKf5a-_JdLl5ZX0UM0UnwGiJ4qiXEhzactSDj6HQMrWhAFi01B6WpOYssrINvci6n-E3YiRjKeMrEDaIKpxXsZ0FP8mCaNSKMaXX76WbgqD8AXNfZ1LzyTK4QiGwbecMpjXXhtx_bqG_I25tQKM84xLHkgQb_mQ0sF3C9B6WWDuFg-flcXn2nIt-CDlNOG6ZU_KkC8O2g28UC3CryQ_CqqqRxpAwinfTbYky15SFlx02H4GRsNdyZ6AzzNgCYnhBL67GC3x2GLQ4K8mnNI6zrFGOvLG_ZAc5y1OsZQ-lkv69PD7JKfBr_ts__kpfbg6lJrIe62452-OC0aCRliRfyXF9BXLeF_0NcnyVI6BxYQGuFHeipdLma8hhqU8x8cAQpJHfClPW6I_CaPEiyArMG-VoaXsEX-zYmmeBJXqy5pyqBUL-ZbRmLDdTRqlrEK8u7u5u7m_b2Ey8NMkEFAhjqBtiQPjtAtaZ9HEVaeSpqrvp9LMVnTHtNSZqxqz9xf9IK6RVWCCvm6iAbvQdwf19wEetWDvDRiKpc9MTXNs0-kYaGI_qu-eDqBOYAGvvM2RZmiGqh4LVESqOHTtSEQCkK28yUyx1HpoyOrgrB1gRBNo-zPK0fHXDagrxUpMrjer8QI5AHq14ZW8arV4Zjjq7XVPrNdigqPjnTCWvqxx84xmEKYJv8cjINpViOUSs2Lg5f4auBRnxXwqYRsJSEKmUrFbIkH9iX6vd5hmb1_b9BEPomthK70Dt_i1YAmebCM0leIy1SEi_Ah7PbARJhtE20yPsLo_PNJkM77olEcwvOoQrODxvMyJj22tHVS5da2ZYuu2Zru6bhpTCaeOY1uGbWi6W-wnR5mp2sxWHdc0OvupMjfMZCkXtoYXYZQi5rFb9yuGfbpVt3SVkGiYgEq-GN0aVWmkrxjtaBPd4442uf_NVGn2BBNRmm5PQBK8UPUi6xdWCesmigVqkUDAnF4a-kw4TZO-T9u2jyMFt2bx6_SgbzkkPvyRx17HonjiYbPq28O-SiaaqhdnFf7pljWVVMWcdYoy4k_HdE840A9EmZ3DgJNs08_fMszQ80VYN3mXzNQgEDAF5490teYjoTW4MyC3hG1GlrCBfcp5hhe7M5A3eE3aFBeU7rlnaLYhLjgszqOmBe4S5IW-E4Yt5IrR9ukRFTwJzSBIkyOmRpFihALOZ5T3swhDF4cI61YjdBY3DchOaGRdRNkERpYA8ABlAkWWpeMQQWKv66H8CK-_BWroihPSKFrstqAONcIGoA0dcQ1AP_RHQzVP3yIbPeOgp-kHvcHLX6NntvQc-3x_1kHv8j-4s1s3zPOdOa0gXXfQW6GGn2rFh0S-DfA76i6geBzK85BEGUxlkvP0aZf48pyzHBpQ_TVeo378C6WSmNU)](https://mermaid-js.github.io/mermaid-live-editor/edit/#pako:eNqdV-mO2zYQfhVBQQBv61V1SzaQBboXFsii-bFGESAOCkoa2ax1OBS1u84iL5VH6JN1dNkSZcluacAQNd9cH4dD6k320wDkuZxxwuGWkhUj8eWzvkyWiYRjnTKf5a-_JdLl5ZX0UM0UnwGiJ4qiXEhzactSDj6HQMrWhAFi01B6WpOYssrINvci6n-E3YiRjKeMrEDaIKpxXsZ0FP8mCaNSKMaXX76WbgqD8AXNfZ1LzyTK4QiGwbecMpjXXhtx_bqG_I25tQKM84xLHkgQb_mQ0sF3C9B6WWDuFg-flcXn2nIt-CDlNOG6ZU_KkC8O2g28UC3CryQ_CqqqRxpAwinfTbYky15SFlx02H4GRsNdyZ6AzzNgCYnhBL67GC3x2GLQ4K8mnNI6zrFGOvLG_ZAc5y1OsZQ-lkv69PD7JKfBr_ts__kpfbg6lJrIe62452-OC0aCRliRfyXF9BXLeF_0NcnyVI6BxYQGuFHeipdLma8hhqU8x8cAQpJHfClPW6I_CaPEiyArMG-VoaXsEX-zYmmeBJXqy5pyqBUL-ZbRmLDdTRqlrEK8u7u5u7m_b2Ey8NMkEFAhjqBtiQPjtAtaZ9HEVaeSpqrvp9LMVnTHtNSZqxqz9xf9IK6RVWCCvm6iAbvQdwf19wEetWDvDRiKpc9MTXNs0-kYaGI_qu-eDqBOYAGvvM2RZmiGqh4LVESqOHTtSEQCkK28yUyx1HpoyOrgrB1gRBNo-zPK0fHXDagrxUpMrjer8QI5AHq14ZW8arV4Zjjq7XVPrNdigqPjnTCWvqxx84xmEKYJv8cjINpViOUSs2Lg5f4auBRnxXwqYRsJSEKmUrFbIkH9iX6vd5hmb1_b9BEPomthK70Dt_i1YAmebCM0leIy1SEi_Ah7PbARJhtE20yPsLo_PNJkM77olEcwvOoQrODxvMyJj22tHVS5da2ZYuu2Zru6bhpTCaeOY1uGbWi6W-wnR5mp2sxWHdc0OvupMjfMZCkXtoYXYZQi5rFb9yuGfbpVt3SVkGiYgEq-GN0aVWmkrxjtaBPd4442uf_NVGn2BBNRmm5PQBK8UPUi6xdWCesmigVqkUDAnF4a-kw4TZO-T9u2jyMFt2bx6_SgbzkkPvyRx17HonjiYbPq28O-SiaaqhdnFf7pljWVVMWcdYoy4k_HdE840A9EmZ3DgJNs08_fMszQ80VYN3mXzNQgEDAF5490teYjoTW4MyC3hG1GlrCBfcp5hhe7M5A3eE3aFBeU7rlnaLYhLjgszqOmBe4S5IW-E4Yt5IrR9ukRFTwJzSBIkyOmRpFihALOZ5T3swhDF4cI61YjdBY3DchOaGRdRNkERpYA8ABlAkWWpeMQQWKv66H8CK-_BWroihPSKFrstqAONcIGoA0dcQ1AP_RHQzVP3yIbPeOgp-kHvcHLX6NntvQc-3x_1kHv8j-4s1s3zPOdOa0gXXfQW6GGn2rFh0S-DfA76i6geBzK85BEGUxlkvP0aZf48pyzHBpQ_TVeo378C6WSmNU)
