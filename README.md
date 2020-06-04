# AVA APIs: Postman collections

This repo contains Postman collections for all eight of the Ava JSON-RPC APIs.


**Motivation:** I have noticed that users are struggling with 

(a) inputting correct unix timestamps to API calls (on Mac especially, but also on Ubuntu), and 

(b) incrementing payerNonce.

(c) Generally speaking, the most common source of error is manual data entry. Having these calls saved and correctly formatted avoids this.

The following Postman collections automate these, and in general greatly ease the workload for interacting with AVA.


## 20-06-01 Denali testnet update!

**Introducing teams**
There is now a [team for AVA APIs on Postman](https://app.getpostman.com/join-team?invite_code=90f1199fc9ef3e79be5c52b7674dfcec)! Joining this team does the following:

- it enables people to use the AVA environment and all collections in their most up-to-date form, instead of having to manually check the repo, manually input variables, and so forth.

- collaborate on changes and enhancements to API calls (if you want to)

- gain access to the closest thing right now to a self-hosted AVA wallet GUI


**Tips if you join the team**

1) To prevent everyone learning your password, privkey, etc.: in Postman, go to Settings --> General, and uncheck "automatically persist variable values. For the same reason, do not "persist" those variables from the environment modal.

2) If you want to make a change to a call, to avoid surprising people, fork the collection: in the sidebar, hover over the collection, click "..." --> create a fork.


To join the AVA APIs team on Postman, [click here](https://app.getpostman.com/join-team?invite_code=90f1199fc9ef3e79be5c52b7674dfcec).


### Changelist:

- Added the AVA environment to the repo. No need to manually input variables!

- Tests passed: tested the steps from a fresh start through to setting up a validator on Denali, and from exporting coins from the P-Chain back to the X-Chain. The collections now accomplish this more or less robotically.

- MOAR automation, less copy+paste: I added scripts to very many calls, in order to automatically populate environment variables with the response data provided in calls. (In  have, however, avoided automating where the implied use and sequence are not unambiguous. No need to overcomplicate and/or require people to fiddle with scripts unnecessarily.)

- Scripting fix: I added the script that automatically increments "payerNonce" to two calls (which I'd previously neglected to add it to): `platform.addDefaultSubnetValidator`, and `platform.importAVA`.

- Added an environment to the AVA APIs team, so that users do not have to manually create variables before use. 





It is not necessary to download this repo. If you sign up to the team, these collections (and also the environment) will automatically sync over. Alternatively, if you use Postman, you may simply click on any of the following links to add the most up-to-date version of a collection to your library:


- [Admin API](https://documenter.getpostman.com/view/1224601/SztHW53B)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/8dd8f41bc190fd42607e)


- [AVM (X-Chain) API](https://documenter.getpostman.com/view/1224601/SztHW57V)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/8cf12f11e821bbbf7e3c)


- [EVM (C-Chain( API](https://documenter.getpostman.com/view/1224601/SztHW57Y)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/3ca30db566d1f4dcdf90)


- [IPC API](https://documenter.getpostman.com/view/1224601/SztHW57Z)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/8a4f6ad5cfd004175d71)


- [Keystore API](https://documenter.getpostman.com/view/1224601/SztHW57c)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/d82c54eebe28afb54927)


- [Metrics API](https://documenter.getpostman.com/view/1224601/SztHW5Bu)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/25b6eed477b652661a0c)


- [Platform (P-Chain) API](https://documenter.getpostman.com/view/1224601/SztHW5Bv)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/35c691dc2fc821d7f1a5)


- [Timestamp API](https://documenter.getpostman.com/view/1224601/SztHW5Bw)

&nbsp;&nbsp;&nbsp;&nbsp;[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/0b79452b337de89a4c16)


**Note:** these are static links and so will not automatically update as the collections are improved. To get updates, watch this repo: I will replace the links with fresh ones when collections are enhanced.


## How to use these collections

1) To avoid interminable editing of many calls, username and password are implemented assuming the environment variables {{username}} and {{password}} respectively. To have Postman insert your username and password wherever required, create the environment variables "username" and "password", using the "current value" field to hold your username and password.

2) A number of attributes (e.g. address, txid, balance, user...) have been implemented as environment variables. These typically autopopulate as a result of making calls, but you may manually enter ivalues at any time. To do so from existing call data, select and right-click on a relevant value in a call and assign it to the corresponding variable in the context menu. Doing this will cause subsequent calls to automatically populate with the specified values.

3) The usefulness of the above variables may be considerably enhanced through the use of scripting.

4) Given widespread difficulty with inserting correctly-formatting unix timestamps into certain calls, I have implemented scripts where necessary to automatically insert unix timestamps, adding 5 minutes and 16 days from the current time by default (but users can alter these values at will from the "pre-request script tab" of the relevant calls).

5) Due to some users having trouble with setting the correct "payerNonce", I have implemented scripts where necessary to automatically increment "payerNonce". Note, however, that (a) it will increment even if a call fails, and (b) it will not reset per user or account, so manually inputting values for the "payerNonce" environment variable may be necessary at times. For a fresh user, the "payerNonce" variable should be set to 0. For an existing user, to ensure that the "payerNonce" variable accords with your P-Chain account's state, you can call "platform.listAccounts" to set the "payerNonce" variable to the correct value.

6) To avoid confusion when exporting coins from the P-chain to the X-chain, I have implemented a script on platform.exportAVA to remove "X-" from X-chain addresses, along with a corresponding environment variable, "noXaddress", keeping this address format distinct from the usual format handled by the variable "address".

7) The majority of calls have scripts that populate environment variables with values returned in the responses to calls. These may be deleted or altered at will (but please fork the collection before doing so, or else it may impact other users' work.)

8) If you prefer not to use environment variables, you may manually replace variables (signified by the use of double curly brackets, eg. {{username}}, {{password}}, and so forth) with static values.


