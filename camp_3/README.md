<div align="center">
    <h1>Camp 3: StarkNet</h1>

|Presentation|Video|Try what you learned
|:----:|:----:|:----:|
|[September 2022](https://drive.google.com/file/d/1_AQq4ulTmB0VAszmauvYUHEVjwdAgMim/view?usp=sharing)|StarkNet Basecamp [p1 (September 2022)](https://drive.google.com/file/d/1w9ysR38Dz4Z9gvHC46xSHbr06B36nUWp/view?usp=sharing), [p2 (September 2022)](https://drive.google.com/file/d/185MMFmItlOE5qER8P2vhtVjKiH6Glj1G/view?usp=sharing)|Make your own [Messaging Bridge](https://github.com/starknet-edu/starknet-messaging-bridge). Test your [Account Abstraction capacity](https://github.com/starknet-edu/starknet-accounts)|

</div>

### Topics

<ol>
    <li><a href="#blocks">Blocks</a></li>
    <li><a href="#tx_lifecycle">The Lifecycle of Transactions</a></li>
    <li><a href="#starknet_os">StarkNet OS</a></li>
    <li><a href="#state">State Transition/Fees</a></li>
    <li><a href="#accounts">Account Contracts</a></li>
    <li><a href="#aa">Account Abstraction</a></li>
    <li><a href="#l1l2">L1-L2 Messaging</a></li>
</ol>

<h2 align="center" id="blocks">Blocks</h2>

<h2 align="center" id="tx_lifecycle">The Lifecycle of Transactions</h2>

On StarkNet Alpha the two types of transactions are `DEPLOY` or `INVOKE`. They go through the following lifecycle as they are submitted from the clients to the sequencer:

<div align="center">
    NOT_RECEIVED -> RECEIVED -> PENDING -> REJECTED || ACCEPTED_ON_L2 -> ACCEPTED_ON_L1
</div>


<h2 align="center" id="starknet_os">StarkNet OS</h2>

The StarkNet OS is the Cairo program that runs StarkNet. The OS handles everything which is done on the network — contract deployment, transaction execution, L1<>L2 messages and more.

<h2 align="center" id="state">State Transition/Fees</h2>

<h2 align="center" id="accounts">Accounts</h2>

<h2 align="center" id="aa">Account Abstraction</h2>

**Disclaimers: This tutorial cites various stakeholders, any errors or misunderstandings in this tutorial are the fault of interpretation.*

* Most Ethereum users use centralized exchanges because managing a self-custody wallet is difficult; this is not self-custody. The current status quo risks making the next wave of users dependent on centralized exchanges ([Julien, Devcon 6](https://www.youtube.com/watch?v=OwppworJGzs)).
* The imminent arrival of quantum computers will force the cryptographic ecosystem to move to quantum-proof signatures. The stark curve is one way it can be done.

In 5 years it would be bizarre that we used to secure our assets by writing 12 words on paper. StarkNet is leading the way in implementing AA at the protocol level (not at the application level as with current EIPs on L1): it is the "proving ground" for what AA will look like in the future ([AA Panel, Devcon 6](https://app.devcon.org/schedule/9mvqce)).


### What is Account Abstraction?

> Definition 1: AA is when a **smart contract can pay for its own transactions** ([Martin Triay, Devcon 6](https://www.youtube.com/watch?v=Osc_gwNW3Fw)). In other words, abstract contracts (or account smart contracts) can pay for transactions. Note, it is not the same as Externally Owned Accounts or Smart Wallets.

> Definition 2: AA is **validation abstraction**. In L1 there is only one way to validate transactions (retrieve an address from a signature, look at that address in the state, determine if the nonce is OK for the transaction that was sent and if the account has enough balance to perform the transaction). With AA, you **abstract the validation process**: use different types of signatures, cryptographic primitives, execution processes, etc. ([lightclient, Devcon 6](https://app.devcon.org/schedule/9mvqce)).

**Note: In computing, the term abstraction is used to generalize something. In this case, we are generalizing smart contracts: from the existence of Externally Owned Contracts (EOA) and Contract Accounts (CA) to simply smart contracts.*


### So what?

According to:
* Martin Triay (Open Zepellin), AA means [huge improvements in onboarding, user experience, and security](https://www.youtube.com/watch?v=Osc_gwNW3Fw). AA is the future of crypto UX and security.
* Julien Niset (Argent), AA means scaling self-custody which is [a requirement for onboarding the next billion users](https://www.youtube.com/watch?v=OwppworJGzs).
* Vitalik, [smart wallets should be the default](https://app.devcon.org/schedule/9mvqce) and AA is the key step. 
* Yoav (Ethereum Foundation), [AA is key security](https://app.devcon.org/schedule/9mvqce).
  

###  Self-custody: own the keys, own the assets

Self-custody is hard and necessary. Crypto is about digital ownership: you own your assets. The principle is normally depicted with the motto: not your keys not your asset. The principle is great. However, the humans will always lose and forget passwords ([Julien, Devcon 6](https://www.youtube.com/watch?v=OwppworJGzs)). From experts to beginners, everyone looses their passwords or keys. It is as true since web2 and will keep being truth in web3. Julien goes as far as saying that "ordinary users should never handle key management, and if Ethereum doesn’t transition away from EOAs we’ll live in a world where only the few use self-custody and the rest use centralized exchanges" ([2022](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/)). 

In Ethereum, and other L1s, users lose their keys and recovery phrases; and that is it, the user can not recover her account's assets. There is no "I forgot my keys, help me recover my account." Whose idea was that the private key was a hard requirement? According to [Julien](https://www.youtube.com/watch?v=OwppworJGzs), the problem is at the heart of the EVM (Ethereum Virtual Machine). We will go back to this later. With AA the private key will soon be a thing of the past. 


### Use cases (some of them, invent one!)
AA promises to put programmability into every Ethereum wallet, and unlock new frontiers for both developers and users ([AA Panel, Devcon 6](https://app.devcon.org/schedule/9mvqce)). 

Among other things, AA allows:
* Social recovery: In case a user's private key is lost or compromised, AA allows wallets to add mechanisms to securely replace the key controlling the account. Never worry about seed phrases again ([Julien Niset, 2022](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/))!
* Key rotation: If your keys are compromised, instead of moving all the assets, you can rotate the keys and that is it. (XXX look more about this)
* Session keys: Signing with your face or finger to your cellphone or your favorite apps is possible with AA. Session keys are a set of permissions given to a website so, for example, you can sign in once and then the website can act on our behalf without you having to sign each time each transactions. This is Web2 experience.
* Guardians: XXX
* Custom transaction validation schemes.
  * Different signature schemes: You can use ethereum signatures, Bitcoin signatures, both if you want. The user could prefer a more gas-efficient signature, or a quantum-resistant one.  Use the secure enclave of iOS and Android devices to turn every phone into a hardware wallet ([Martin Triay (Devcon 6)](https://www.youtube.com/watch?v=Osc_gwNW3Fw), [Julien (2022)](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/)).
  * Multisignature: Change who can sign each week. Support fraud monitoring; inspect every transaction to make sure it complies to defined security rules, and prevent users from sending assets to a scam address or incorrect contract. ([Martin Triay (Devcon 6)](https://www.youtube.com/watch?v=Osc_gwNW3Fw), [Julien (2022)](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction)).

These are just some ideas. More is still to come.

### Security

There are my ways AA helps security in Ethereum. The following were mentioned by [Yoav at Devcon 6](https://app.devcon.org/schedule/9mvqce):

* Key management: Being able to add devices to your wallet so your wallet is not associated with the seed phrase, but if you loose your ohone you can access with your computer. This improves security,
* Different signature and validation schemes: You could, for example, spend small amounts freely but if you are sending a large amount the dapp or wallet could ask for another type of signature similar to 2 Factor Authorization. This is common in centralized excahnges. 
* Different security policies for different types of users: With EOAs (L1) we only have a single policy; if you have the key then do anything if you do not have it then you can not do anything. With AA, for example, we could create a security scheme for enterprise accounts and another one for individual users. Again, copy good practices in the banking and web2 sector.
* Different security policies for different devices: For example, a phone can send a maximum amount of tokens and a computer there is a limit un less you validate in some way (2FA). For this to happen we need to be able to implement different signature schemes according to each device (e.g., a computer does not use the same curve as an android phone). The EOAs support only a type of curve which is incompatible with most devices. With AA you can use several devices with the same account. Users will not longer have a different wallet on each device; one for the computer, one for the phone, one for the Ledger. 

### Why has it not been implemented in Ethereum's L1 yet?

According to Julien Niset ([2022](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/)), the key is to eliminate EOAs. No EIP has yet addressed this. It is understandable since this would implicate multiple changes to the heart of the protocol; and day by day, as the value secured by Ethereum increases, implementing AA gets more difficult due to the coordination required ([Julien Niset, 2022](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/)).

If it is so important, then why does Ethereum already supports it? This is an example of the limitations of the EVM that can be surpased by a new Virtual Machine such as the Cairo VM. Proposals to implement AA have been made since the early days of Ethereum and they have constantly been "repeatedly pushed back in favour of more urgent changes." ([Julien Niset, 2022](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/)). It is uncertain it will be implemented in next Ethereum versions even after the Merge.

The creation of new L2 VMs focused on scalability allowed for advances in its implementation; StarkNet and ZKSync have native AA inspired by EIP4337, considered the best proposal by experts such as Argent's Julien Niset ([2022](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction/)). It seems as if key proponents of AA, like Julien, have lost hope that EOAs are eliminated and AA is implemented at the core of Ethereum; Argent is now pushing for the widespread adoption of AA trough L2s like StarkNet.

### Devcon 6

AA was one of the hottest topics at Devcon 6 (2022). There were at least 6 talks, workshops and panels (one of them with Vitalik) on the subject. Of these two were addressed directly from AA on StarkNet, and they all acknowledge AA on StarkNet.
* [Martin Triay, Open Zeppelin: Account Abstraction in StarkNet](https://www.youtube.com/watch?v=Osc_gwNW3Fw) (StarkNet oriented).
* [Vitalik Buterin, David Hoffman (Bankless), Julien Niset (Argent), Yoav Weiss (Ethereum Foundation), lightclient (Geth): Account Abstraction Panel](https://www.youtube.com/watch?v=WsZBymiyT-8&feature=emb_imp_woyt).
* [Liraz, Yoav Weiss (Ethereum Foundation): ELI5: Account Abstraction](https://www.youtube.com/watch?v=QuYZWJj65AY).
* [(ETH Global) Yoav Weiss (Ethereum Foundation), Dror Tirosh: Ethereum Foundation 🛠 Account abstraction: building an ERC-4337 wallet](https://www.youtube.com/watch?v=xHWlJiL_iZA).
* [Dror Tirosh, Liraz: Account Abstraction: Making Accounts Smarter](https://app.devcon.org/schedule/nz3pyp).
* [Ivo Georgiev, Ambire Wallet: The Future of Wallets: MPC vs Smart Wallets](https://archive.devcon.org/archive/watch/6/the-future-of-wallets-mpc-vs-smart-wallets/?tab=YouTube).
* [Danno Ferrin, Hedera Hashgrap: What Alternative Blockchains Compatibility with Ethereum Tooling Can Teach Us About Ethereum's Future](https://www.youtube.com/watch?v=KqE9HN4QGpM).
  

### AA is already here, enjoy! 

Now that we know better the concept of AA, let's actually code it in StarkNet.

As it was mentioned before, StarkNet possess AA natively. The design has been notably led by Starkware, Open Zeppellin, and Argent.

### The proccess

We will perform **counterfactual deployment**. That is:

1. Calculate the account contract's address before deployment.

A contract address in the StarkNet network is a unique identifier of the contract and is a hash of (more details in [the documentation](mentation/develop/Contracts/contract-address/) and [actual implementation in Python](https://github.com/starkware-libs/cairo-lang/blob/13cef109cd811474de114925ee61fd5ac84a25eb/src/starkware/starknet/core/os/contract_address/contract_address.py#L40)):
* Prefix - the ASCII encoding of the string “STARKNET_CONTRACT_ADDRESS”.
* Deployer address - currently always zero.
* Salt - random number (felt) used to distinguish between different instances of the contract.
* Class hash - hash chain of the definition of the class (more [here](https://docs.starknet.io/documentation/develop/Contracts/contract-hash/)).
* Constructor calldata hash - array hash of the inputs to the constructor.

This means we can calculate the contract address of the account contract we want to deploy even before deploying. This is what we do when we initialize an account contract:

```Bash
starknet new_account --network alpha-goerli --account ALIAS --wallet starkware.starknet.wallets.open_zeppelin.OpenZeppelinAccount
```

This yields something like:

```Bash
Account address: 0x006b27f2455d175f1c9b39568838ee0c1dfba34ca29f489690e40ee69220f15c
Public key: 0x07f90c757da3498bfa61b393e1048ace09d9729f9fc75d2a5dc6eb590852643e
Move the appropriate amount of funds to the account, and then deploy the account
by invoking the 'starknet deploy_account' command.

NOTE: This is a modified version of the OpenZeppelin account contract. The signature is computed
differently.
```

Now we have the account contract's address (([this is the line](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/wallets/open_zeppelin.py#L107) where the address is calculated in the repo)) that we can fund; if using the testnet we can use the [faucet](https://faucet.goerli.starknet.io/). We are using the default account contract structure created by Open Zeppelin (a bit modified) which you can find in the [third_party library](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/third_party/open_zeppelin/Account.cairo). In the next sections we will create our own account contracts. 

2. Send funds to that address, eventhough it has no contract yet (it has not yet been deployed);

For example, we can send funds using the [testnet faucet](https://faucet.goerli.starknet.io/).

3. The contract pays for its deloyment transaction if it passes `__validate_deploy__`; and 

Deploy the account contract with:

```Bash
starknet deploy_account --network alpha-goerli --account ALIAS --wallet starkware.starknet.wallets.open_zeppelin.OpenZeppelinAccount
```

If the conditions defined in the `__validate_deploy__` entrypoint are met, the account contract is deployed. In the case of the Open Zeppelin account contract the signature should be valid for the contract to be deployed:

```Bash
@external
func __validate_deploy__{
    syscall_ptr: felt*, pedersen_ptr: HashBuiltin*, range_check_ptr, ecdsa_ptr: SignatureBuiltin*
}(class_hash: felt, contract_address_salt: felt, _public_key: felt) {
    let (tx_info) = get_tx_info();
    is_valid_signature(tx_info.transaction_hash, tx_info.signature_len, tx_info.signature);
    return ();
}
```

4. The account contract is deployed ([Martin Triay, (Devcon 6)](https://www.youtube.com/watch?v=Osc_gwNW3Fw)).

If successfully deployed, we get:

```Bash
Sending the transaction with max_fee: 0.000000 ETH (323076307108 WEI).
Sent deploy account contract transaction.

Contract address: 0x006b27f2455d175f1c9b39568838ee0c1dfba34ca29f489690e40ee69220f15c
Transaction hash: 0x3dc6e579d7b4204907de859d1a12e42132853b9827e7203487740d51e957eed
```

Please note currently the StarkNet CLI only works with the [OpenZeppelin account contract](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/third_party/open_zeppelin/Account.cairo). If we want to deploy our own account contracts we need to deploy them using a different method. More on the next sections. 

Now we will examine the inner workings of the Open Zeppelin contract and proceed create our own account contracts.

### Using the Open Zeppelin standards

Although account contracts are nothing more than smart contracts, they have methods that set them apart from other smart contracts. This is the [Open Zeppelin IAccount contract interface](https://github.com/OpenZeppelin/cairo-contracts/blob/release-v0.4.0b/src/openzeppelin/account/IAccount.cairo) adopted also by Argent (it implements [EIP-1271](https://eips.ethereum.org/EIPS/eip-1271)):

```Rust
struct Call {
    to: felt,
    selector: felt,
    calldata_len: felt,
    calldata: felt*,
}

// Tmp struct introduced while we wait for Cairo to support passing `[Call]` to __execute__
struct CallArray {
    to: felt,
    selector: felt,
    data_offset: felt,
    data_len: felt,
}


@contract_interface
namespace IAccount {
    func supportsInterface(interfaceId: felt) -> (success: felt) {
    }

    func isValidSignature(hash: felt, signature_len: felt, signature: felt*) -> (isValid: felt) {
    }

    func __validate__(
        call_array_len: felt, call_array: AccountCallArray*, calldata_len: felt, calldata: felt*
    ) {
    }

    func __validate_declare__(class_hash: felt) {
    }

    func __execute__(
        call_array_len: felt, call_array: AccountCallArray*, calldata_len: felt, calldata: felt*
    ) -> (response_len: felt, response: felt*) {
    }
}
```

And this is the public API ([find the complete preset here](https://github.com/OpenZeppelin/cairo-contracts/blob/release-v0.4.0b/src/openzeppelin/account/presets/Account.cairo)):

```Rust
namespace Account {
    func constructor(publicKey: felt) {
    }

    func getPublicKey() -> (publicKey: felt) {
    }

    func supportsInterface(interfaceId: felt) -> (success: felt) {
    }

    func setPublicKey(newPublicKey: felt) {
    }

    func isValidSignature(hash: felt, signature_len: felt, signature: felt*) -> (isValid: felt) {
    }

    func __validate__(
        call_array_len: felt, call_array: AccountCallArray*, calldata_len: felt, calldata: felt*
    ) -> (response_len: felt, response: felt*) {
    }

    func __validate_declare__(
        call_array_len: felt, call_array: AccountCallArray*, calldata_len: felt, calldata: felt*
    ) -> (response_len: felt, response: felt*) {
    }

    func __execute__(
        call_array_len: felt, call_array: AccountCallArray*, calldata_len: felt, calldata: felt*
    ) -> (response_len: felt, response: felt*) {
}
```

Note that the [default account contract](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/third_party/open_zeppelin/Account.cairo) used by StarkNet and mainly developed by Open Zeppelin has this same structure.

Let's examine the entry points (functions):

* `constructor`: It is not a requirement.
  * `publicKey: felt`: While the interface is agnostic of signature validation schemes, this implementation assumes there’s a public-private key pair controlling the Account. That’s why the constructor function expects a `public_key` parameter to set it. Since there’s also a `setPublicKey()` method, accounts can be effectively transferred ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).
* `getPublicKey`: Returns the public key associated with the Account ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).
* `supportsInterface`: Returns TRUE if this contract implements the interface defined by `interfaceId`. Account contracts now implement ERC165 through static support (see [Account differentiation with ERC165](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts#account_differentiation_with_erc165)) ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).
* `setPublicKey`: Sets the public key that will control this Account. It can be used to rotate keys for security, change them in case of compromised keys or even transferring ownership of the account ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).
* `isValidSignature`: This function is inspired by EIP-1271 and returns TRUE if a given signature is valid, otherwise it reverts. In the future it will return FALSE if a given signature is invalid ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).
* `__validate__`: Allows you to define an arbitrary logic to determine if a transaction is valid or not. They can not read other contracts storage, this helps as anti-spam. For example, a lot of transactions can depend on the storage of a contract, therefore if the storage changes then everything that depends on it start failing. The account contract will first call `__validate__` upon receiving a transaction. It receives as arguments (calldata):
  * `call_array_len: felt` - number of calls.
  * `call_array: AccountCallArray*` - array representing each `Call`.
  * `calldata_len: felt` - number of calldata parameters. Remember calldata are the arguments used to call a function.
  * `calldata: felt*` - array representing the function parameters.
* `__validate_declare__`: Validates the declaration signature prior to the declaration. As of Cairo v0.10.0, contract classes should be declared from an Account contract ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)). Declare transactions now require accounts to pay fees.
  * `class_hash: felt`:
* `__execute__`: This is the only external entrypoint to interact with the Account contract. If `__validate__` is successful `__execute__` will be called. Acts as the state-changing entry point for all user interaction with any contract, including managing the account contract itself ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).
  * Same arguments as `__validate__`. However, `__execute__` returns a transaction response.

We are also using new structs:
1. A single `Call`:

```Rust
struct Call {
    to: felt
    selector: felt
    calldata_len: felt
    calldata: felt*
}
```
Where:

* `to` is the address of the target contract of the message.
* `selector` is the selector of the function to be called on the target contract.
* `calldata_len` is the number of calldata parameters.
* `calldata` is an array representing the function parameters ([Open Zeppelin Docs, 2022](https://docs.openzeppelin.com/contracts-cairo/0.5.0/accounts)).


2. `AccountCallArray`, a calls array:

```Rust
struct AccountCallArray {
    to: felt
    selector: felt
    data_offset: felt
    data_len: felt
}
```
Where:
* `to` and `selector` are the same as in `Call`.
* `data_offset` is the starting position of the calldata array that holds the `Call`'s calldata.
* `data_len` is the number of calldata elements in the `Call`.


###Counterfactual deployment from inside

Let us deploy the default account contract, inspired by the Open Zeppelin implementation, with alias `second-account`, to the Goerli 2 testnet. The  `--wallet starkware.starknet.wallets.open_zeppelin.OpenZeppelinAccount` flag indicates we will use the default account contract, currently we can only use this contract with the CLI.

```Bash
starknet new_account --feeder_gateway_url https://alpha4-2.starknet.io --gateway_url https://alpha4-2.starknet.io --network_id 1536727068981429685321 --account second-account --wallet starkware.starknet.wallets.open_zeppelin.OpenZeppelinAccount
```

We get:

```Bash
Account address: 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9
Public key: 0x066ed5a84f995a2dcd714b505dc165a8df71473ebc374dbe5fe973631198ba72
Move the appropriate amount of funds to the account, and then deploy the account
by invoking the 'starknet deploy_account' command.

NOTE: This is a modified version of the OpenZeppelin account contract. The signature is computed
differently.
```

[OPTIONAL] We can go deeper into examining the default Open Zeppelin account contract to get the class hash, salt and constructor calldata that are used to calculate its address. [`src/utils/contract_address.py`](../../../src/utils/contract_address.py) is a copy of the [`contract_address.py`](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/core/os/contract_address/contract_address.py) library from the Starkware library. We added print statements in the `calculate_contract_address()` function to get the class hash, salt, and constructor calldata. If you wish to use it, go to where your OS stores your Python packages (likely `site-packages`) and replace `/starkware/starknet/core/os/contract_address/contract_address.py` with our [`src/utils/contract_address.py`](../../../src/utils/contract_address.py). Then, when we defined our account contract with `starknet new_account ...` we also get:

```Bash
Class Hash: 895370652103566112291566439803611591116951595367594863638369163604569619773
Salt: 462250451139519919709009935198618602877233823783070820758189518720702799406
Constructor calldata: [2909704878250883580952868877137725986814034606621060536770963048574421088882]
```

All three properties are in felt format. You can manually convert them into their hex representations, if you wish, with the [stark-utils](https://www.stark-utils.xyz/converter) converter. The Open Zeppelin default account contract requires a public key in its constructor ([see implementation](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/third_party/open_zeppelin/Account.cairo#L105)), if we wish, with our own account contracts, we can not add this requirement. The contract we defined above has a public key `0x066ed5a84f995a2dcd714b505dc165a8df71473ebc374dbe5fe973631198ba72` once we converted the above felt into hex format.

Calculating the address is the key of this first step in counterfactual deployment. Remember, it has not yet been deployed, we only calculated the address and added this new account to the `.starknet_accounts/starknet_open_zeppelin_accounts.json` file. It is key to closely follow the `starknet_open_zeppelin_accounts.json` since there we can find our created account contracts; you will find it in your root directory, for example, `/Users/espejelomar/.starknet_accounts/starknet_open_zeppelin_accounts.json`. `starknet_open_zeppelin_accounts.json` shows relevant information for the creation of each account contract. For example, for the `first-account` we created previously we have:

```Bash
"1536727068981429685321": {
        "second-account": {
            "private_key": "XXX",
            "public_key": "0x66ed5a84f995a2dcd714b505dc165a8df71473ebc374dbe5fe973631198ba72",
            "salt": "0x1059fde2a4da7c421dd6dbe8af873a2977c6008c7a09e61db1c5a45d25ede2e",
            "address": "0x2b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9",
            "deployed": false
        }
    },
```
`1536727068981429685321` is the chain_id for goerli. Note it says `"deployed": false` since we have not deployed the contract. 

If we use the same compiled code, salt (this is the main function of the salt), and constructor call data then we should be able to calculate the same address. The `get_address` function in [`src/utils/accounts_utils.py`](../../../src/utils/accounts_utils.py) (next step: create a new library for helping users more easily create account contracts 🚀) is able to calculate the address of any contract without deploying it. We will get the same address for the Open Zeppelin account contract if we get into Python mode in our terminal, `python3.9 -i src/utils/accounts_utils.py` (I am using `python 3.9`), and call (notice we reuse the `salt` and `constructor_calldata` we got above, and that we are using the compiled code of the default Open Zeppelin account contract in [`assets/compiled_open_zeppeling_account_contract.json`](../../../assets/compiled_open_zeppeling_account_contract.json).

```Python
get_address(
    contract_path_and_name = "assets/compiled_open_zeppeling_account_contract.json",
    salt = 462250451139519919709009935198618602877233823783070820758189518720702799406,
    constructor_calldata = [2909704878250883580952868877137725986814034606621060536770963048574421088882],
    deployer_address = 0,
    compiled = True,
)
```

We get:

```Bash
Account contract address: 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9
Class contract hash: 0x01fac3074c9d5282f0acc5c69a4781a1c711efea5e73c550c5d9fb253cf7fd3d
Salt: 0x01059fde2a4da7c421dd6dbe8af873a2977c6008c7a09e61db1c5a45d25ede2e
Constructor call data: [2909704878250883580952868877137725986814034606621060536770963048574421088882]

Move the appropriate amount of funds to the account. Then deploy the account.
```

Everything matches, including the account contract address, to our calculation using `starknet new_account ...`. Great! We now know how we are able to calculate addresses before deploying. This is the most important part of counter factual deployment.

Let's fund the calculated address. We can do this by bridging Goerli ETH from L1 to Goerli 2 in the L2. First, fund your L1 wallet with Goerli ETH (you can use the [Paradigm faucet](https://faucet.paradigm.xyz/api/auth/signin)). Now go into the [Goerli 2 contract in the L1](https://goerli.etherscan.io/address/0xaea4513378eb6023cf9ce730a26255d0e3f075b9#writeProxyContract) and in the external `deposit` function write the amount of ETH you wish to bridge and L2 recipient (our calculated contract address: 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9). Now this contract can pay for its own deployment.

We deploy the account contract to Goerli 2 using Protostar. Add (1) as input the constructor calldata, and (2) as salt our value we had before. If we do not specificate the salt value then Protostar generates a random value and we won´t deploy into our defined contract address.

```Bash
protostar deploy assets/compiled_open_zeppeling_account_contract.json --inputs 2909704878250883580952868877137725986814034606621060536770963048574421088882 --salt 462250451139519919709009935198618602877233823783070820758189518720702799406 --gateway-url https://alpha4-2.starknet.io --chain-id 1536727068981429685321
```

We get:

```Bash
[INFO] Deploy transaction was sent.
Contract address: 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9
Transaction hash: 0x070326e2bed2746fe92847eacf9d04a05cf7b943369afb99f4ad09839f0281c0
```

The contract address is still the same. And now our contract is [deployed in Goerli 2](https://testnet-2.starkscan.co/contract/0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9#overview). Inside StarkScan go to the Portfolio tab to see the ETH we transferred to this address before the deployment.

Now we dominate the Open Zeppelin account contract and how to counterfactually deploy it.

*********
**WIP** DISREGARD THE FOLLOWING
*********


### Examples

Get the nonce with 

```Bash
starknet get_nonce --contract_address 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9 --feeder_gateway_url https://alpha4-2.starknet.io --gateway_url https://alpha4-2.starknet.io --network_id 1536727068981429685321
```

This returns a `0`. What is a nonce? A sequential number attached to the account contract, that prevents transaction replay and guarantees the order of execution and uniqueness of the transaction hash.


Deploy the voting contract with the contract we deployed as an admin and unique voter.

```Bash
protostar deploy build/vote.json --inputs 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9 1 0x02b0fc135cae406bbc27766c189972dd3aae5fc79a66d5191a8d6ac76a0ce8f9 --gateway-url https://alpha4-2.starknet.io --chain-id 1536727068981429685321
```

We get:

```Bash
Contract address: 0x07d960d57c020be3bddba01fce139800590baf8e58b8abdb7b45bdf518b0a16e
Transaction hash: 0x05c8b2a41b0d8fe7dccfa0cfe7be0281e2de22b3ba2dffd0a64c259b45e67171
```

Let's invoke with our new account contract.

```Python
sign_invoke_transaction(
    contract_address=0x07D960D57C020BE3BDDBA01FCE139800590BAF8E58B8ABDB7B45BDF518B0A16E,
    function_name="admin",
    calldata=[],
    signer_address=0x2B0FC135CAE406BBC27766C189972DD3AAE5FC79A66D5191A8D6AC76A0CE8F9,
    private_key=0x7398FB40A1C5B537D97D1E8ED9439B3A3807F02814DDF501C7521AB84E5B4A7,
)
```

Unlike Ethereum [EOAs](https://ethereum.org/en/developers/docs/accounts/#externally-owned-accounts-and-key-pairs), StarkNet accounts don't have a hard requirement on being managed by a public/private key pair.

AA cares more about `who`(i.e. the contract address) rather than `how`(i.e. the signature).

This leaves the ECDSA signature scheme up to the developer and is typically implemented using the [pedersen hash](https://docs.starknet.io/docs/Hashing/hash-functions) and native Stark curve:

The `signature_1` contract has no concept of a public/private keypair. All the signing was done "off-chain" and yet with AA we're still able to operate a functioning account with a populated signature field.




.
.
.
.
.



Unlike Ethereum where accounts are directly derived from a private key, there’s no native account concept on StarkNet.

Instead, signature validation has to be done at the contract level. To relieve smart contract applications such as ERC20 tokens or exchanges from this responsibility, we make use of Account contracts to deal with transaction authentication.


<h2 align="center" id="l1l2">L1-L2 Messaging</h2>


<hr>