# AVA-APIs-Postman
This repository contains intermittent pushes of Postman Collections for the AVA APIs. 

I have noticed many users struggling with 

(a) inputting correct unix timestamps to API calls (on Mac especially, but also on Ubuntu), and 

(b) incrementing payerNonce. 

This Postman collection automates these data, in addition to reducing the chance of formatting calls incorrectly, and in general greatly easing the workload for interacting with AVA.


This repo contains Postman collections for the Ava JSON-RPC APIs.


It is not necessary to download this repo. If you use Postman, you may simply click on any of the following links to add the collections to your library:

-  [![Admin API](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/8dd8f41bc190fd42607e)

- AVM (X-Chain) API: https://www.getpostman.com/collections/8cf12f11e821bbbf7e3c

- Keystore API: https://www.getpostman.com/collections/d82c54eebe28afb54927

- Platform (P-Chain) API: https://www.getpostman.com/collections/35c691dc2fc821d7f1a5


Note that these are static links and so will not be updated as the collections are improved. To get updates, watch this repo.


**How to use these collections:**

1) To avoid interminable editing of many calls, username and password are implemented assuming the environment variables {{username}} and {{password}} respectively. To have Postman insert your username and password wherever required, create the environment variables "username" and "password", using the "current value" field to hold your username and password.

2) A number of attributes (e.g. address, txid, balance, user...) have been implemented as environment variables. The user make exploit this feature by selecting and right-clicking on a relevant value in the response body of a call and assigning it to the relevant variable. Doing this will cause subsequent calls to automatically populate with the specified values.

3) The usefulness of the above variables may be considerably enhanced through the use of scripting.

4) Given widespread difficulty with inserting correctly-formatting UNIX timestamps into certain calls, I have implemented scripts where necessary to automatically insert UNIX timestamps, adding 10 minutes and 2 days from the current time (as per the Quickstart guide's default settings --> https://docs.ava.network/v1.0/en/quickstart/ava-getting-started/#create-a-p-chain-account. These values may be adjusted from the "pre-request script" tab in any calls utilising a timestamp.

5) Due to some users having trouble with setting the correct "payerNonce", I have implemented scripts where necessary to automatically increment payerNonce. Note, however, that (a) it will increment even if a call fails, and (b) it will not reset per user or account, so manually inputting values for the "payerNonce" environment variable may be necessary.

6) To avoid confusion when exporting coins from the P-chain to the _X-chain, I have implemented a script on platform.exportAVA to remove "X-" from X-chain addresses, along with a corresponding environment variable, "noXaddress", keeping this address format distinct from the usual format handled by the variable "address".

7) If you prefer not to use environment variables, you may manually replace instances of {{username}}, {{password}}, and so forth with static values.


