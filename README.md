# AVA APIs: Postman collections

This repo contains Postman collections for all eight of the Ava JSON-RPC APIs.

*Motivation:* I have noticed that users are struggling with 

(a) inputting correct unix timestamps to API calls (on Mac especially, but also on Ubuntu), and 

(b) incrementing payerNonce. 

The following Postman collections automate these, in addition to reducing the chance of formatting calls incorrectly, and in general greatly easing the workload for interacting with AVA.

It is not necessary to download this repo. If you use Postman, you may simply click on any of the following links to add the collections to your library:

- Admin API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/8dd8f41bc190fd42607e)


- AVM (X-Chain) API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/269348fb38988ffa4d2f)


- EVM (C-Chain( API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/269348fb38988ffa4d2f)


- IPC API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/8a4f6ad5cfd004175d71)


- Keystore API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/d82c54eebe28afb54927)


- Metrics API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/25b6eed477b652661a0c)


- Platform (P-Chain) API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/35c691dc2fc821d7f1a5)


- Timestamp API:

&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/0b79452b337de89a4c16)


**Note:** these are static links and so will not automatically update as the collections are improved. To get updates, watch this repo: I will replace the links with fresh ones when collections are enhanced.


## How to use these collections

1) To avoid interminable editing of many calls, username and password are implemented assuming the environment variables {{username}} and {{password}} respectively. To have Postman insert your username and password wherever required, create the environment variables "username" and "password", using the "current value" field to hold your username and password.

2) A number of attributes (e.g. address, txid, balance, user...) have been implemented as environment variables. These typically autopopulate as a result of making calls, but if a variable has no initial value (or an incorrect value) you will need to manually enter it. To do so from existing call data, select and right-click on a relevant value in a call and assign it to the corresponding variable. Doing this will cause subsequent calls to automatically populate with the specified values.

3) The usefulness of the above variables may be considerably enhanced through the use of scripting.

4) Given widespread difficulty with inserting correctly-formatting unix timestamps into certain calls, I have implemented scripts where necessary to automatically insert unix timestamps, adding 10 minutes and 2 days from the current time (as per the Quickstart guide's default settings --> https://docs.ava.network/v1.0/en/quickstart/ava-getting-started/#create-a-p-chain-account). These values may be adjusted from the "pre-request script" tab.

5) Due to some users having trouble with setting the correct "payerNonce", I have implemented scripts where necessary to automatically increment "payerNonce". Note, however, that (a) it will increment even if a call fails, and (b) it will not reset per user or account, so manually inputting values for the "payerNonce" environment variable may be necessary at times.

6) To avoid confusion when exporting coins from the P-chain to the X-chain, I have implemented a script on platform.exportAVA to remove "X-" from X-chain addresses, along with a corresponding environment variable, "noXaddress", keeping this address format distinct from the usual format handled by the variable "address".

7) If you prefer not to use environment variables, you may manually replace variables (signified by the use of double curly brackets, eg. {{username}}, {{password}}, and so forth) with static values.


