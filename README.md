---
description: >-
  MjolNear is the first Open NFT marketplace on NEAR blockchain. You can sell
  and buy NFTs from any other marketplace or collection. This simple guide will
  help you to start.
---

# How to start with MjolNear?

### Which contracts are supported on MjolNear?

Not every contract on NEAR blockchain is NFT contract. There are several standarts that must be implemented by the contract: [NEP-171](https://nomicon.io/Standards/NonFungibleToken/Core), [NEP-177](https://nomicon.io/Standards/NonFungibleToken/Metadata), [NEP-178](https://nomicon.io/Standards/NonFungibleToken/ApprovalManagement) and  [NEP-181](https://nomicon.io/Standards/NonFungibleToken/Enumeration). If contract implements all this standarts, it will become usable and visible on MjolNear and any NFT from this contract can be sold or bought via MjolNear.

### What if I want to create my own NFT contract?

It seems a bit complex on the first look but MjolNear team will provide a complex exmaple on how to create your own NFT contract that will satisfy all the requirements, described in previous section.

1. Go to our [sample repository](https://github.com/MjolNear/simple-nft-contract) on GitHub and fork it using "Fork" button in the top right corner.

![](.gitbook/assets/image.png)

2\. Clone forked repository.

3\. Now go to directory with cloned project and run in terminal: `./build.sh` . It will build the contract.

4\. Now we have to deploy the contract. Write these commands in terminal:

1. `export NEAR_ENV=mainnet`
2. `near login`- use it to login via your NEAR account
3. `near create-account *your NFT contract name* --masterAccount *you account name*`
4. `near deploy --accountId example-contract.testnet --wasmFile out/main.wasm --initFunction new --initArgs '{"owner_id": "*you account name*", "metadata": {"spec": "nft-1.0.0", "name": "*name of your NFT contract*", "symbol": "*symbol of your contract, usually a small word*", "icon": "*URL for icon of your contract*", "base_uri": "*base URI for decentralazed storage of contract additional metadata (for example` [`NFT Storage`](https://nft.storage)`)*", "reference": "*URL to JSON with more info (traits and etc.)*", "reference_hash": "*hash of reference from previous field. It will be used to build link using base_uri*"}}'`- this command will initialize your contract. You must supply the owner\_id in arguments (owner is the only person who can mint NFTs on the contract, usually it is just your account) and metadata (some info about your NFT contract).  &#x20;
   *   &#x20;Arguments example:    &#x20;

       &#x20;    { "owner\_id": "myaccount.near", "metadata": { "spec": "nft-1.0.0", "name": "My First NFT collection!", "icon": "https://cdn-icons-png.flaticon.com/512/1818/1818401.png", "base\_uri": "https://ipfs.io/ipfs", "reference": "https://linktojson.com/myjson.json", "reference\_hash": "aSBsb3ZlIG1qb2xuZWFyIHZlcnkgdmVyeSB2ZXJ5IG11Y2ghISE=" }
5. You contract is ready! Now you can mint any token on it using this command:
   * near call nft\_min



