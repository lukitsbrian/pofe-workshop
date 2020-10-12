---
order: 0
---

# Creating a Proof of File Existence blockchain with Starport

A Proof of File Existence can help prove the authenticity of a certain file at a particular time.

## How can we create a Proof of File Existence?

Creating a proof of file existence can be done performing a SHA256 hash of the file or document you wish to prove exist. We can [assume](https://stackoverflow.com/questions/4014090/is-it-safe-to-ignore-the-possibility-of-sha-collisions-in-practice) that the output of a SHA256 hash function will be unique for each input, and won't be prone to collisions.

```sh
shasum -a 256 file.txt
```

This SHA256 hash of the file is also known as a checksum. When uploading the checksum to the blockchain, we create a proof that we know a file whose hashed content equals this value. This way, we keep the original copy private while ensuring the validity of the file.

## PoFE use cases

- Timestamping documents

    You can take any document and submit the hash as a Proof of File Existence has on the blockchain. That way, you can prove that you had the file at the time when you submitted the block by sharing the file and leting others calculate the checksum. Afterwards, a link to the transaction containing that hash can be shared, proving existence of the file at the time the transaction was performed

- Document Integrity

    Governments or organizations can issue digital legal documents and sumbit the hash as a Proof of File Existence on the blockchain. That way, one can submit a document and an entity can verify its authenticity by querying its hash on the blockchain.

## Application overview

Our application is relatively simple - we want to implement a blockchain where a user can choose a file, hash its contents, and upload the file to the blockchain directly. We also want to give the owner the ability to revoke the claim.

## Requirements

[Starport](https://github.com/tendermint/starport/blob/develop/docs/01%20Introduction/01_starport_introduction/introduction.md) is a tool for scaffolding custom blockchains.

First, we need to [install `starport`](https://github.com/tendermint/starport/blob/develop/docs/install.md), which can be done with either a simple `npm install -g @tendermint/starport`, or `brew install tendermint/tap/starport`.

Now, we can start building our app!