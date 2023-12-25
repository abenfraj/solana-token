# Solana Wallet and Token Configuration Guide

This guide outlines the steps to configure a Solana wallet and create a new token with metadata.

## Set Up Solana CLI
- Install Rust: https://rustup.rs/
- Create your project folder
- Run this command in a new terminal in your new folder (takes long):
  ```bash
  > cargo install spl-token-cli
  ```
- You can go and create your Chainstack account to join a public Solana Devnet network during the installation: https://chainstack.com/
- When the installation is done, you can check if the installation was successful by running this command
  ```bash
  > spl-token --version
  spl-token-cli 3.3.0 (for example)
  ```
- Now you have to install the Solana Tool Suite, you can just follow the instructions of this link: https://docs.solana.com/cli/install-solana-cli-tools
- Again, make sure it successfully installed by running:
  ```bash
  > solana --version
  ```

## Create Wallet and Token
##### → Devnet
```bash
solana config set --url {CHAINSTACK_URL}
```
You can get your Chainstack HTTPS endpoint here if you are trying to deploy on devnet: https://console.chainstack.com/
You can find your HTTPS Chainstack URL in your Solana Devnet node here:
![image](https://github.com/abenfraj/solana-token/assets/72936702/249c03e4-81cb-43dd-a949-33230c03cf31)

##### → Mainnet
```bash
solana config set --url https://api.mainnet-beta.solana.com
```

### Generate a New Keypair
```bash
> solana-keygen new --outfile ./wallet/keypair1.json
```
:warning: <strong>ENTER AND MEMORIZE THE PASSWORD YOU WILL BE ASKED TO INPUT</strong>

### Configure Keypair
```bash
> solana config set --keypair ./wallet/keypair1.json
```
Send SOL to your address if you are on mainnet or get some for free from the devnet faucet here: https://solfaucet.com/

Check the balance of your wallet
```bash
> solana balance {USER_ADDRESS}
```
### Token Creation and Management
Create a new token
```bash
> spl-token create-token
```

Create an account for the token
```bash
> spl-token create-account {TOKEN_ADDRESS}
```

Mint tokens to the account
```bash
> spl-token mint {TOKEN_ADDRESS} {SUPPLY}
```
Check the supply of the created token
```bash
> spl-token supply {TOKEN_ADDRESS}
```

## Transaction Verification
Visit Solana Explorer to check transactions:
##### → Mainnet
https://explorer.solana.com/
##### → Devnet
https://explorer.solana.com/?cluster=devnet

#### Remember to replace the placeholders like `{CHAINSTACK_URL}` and `{TOKEN_ADDRESS}` with your specific details.

## Set the Metadata of your token
In this repository, you will find two important files to set the metadata of your token, main.ts and metadata.json
What you will need to do is:
- Replace the `{TOKEN_NAME}`, `{TOKEN_SYMBOL}`, `{TOKEN_DESCRIPTION}` and `{TOKEN_LOGO}` fields in metadata.json (the logo has to be uploaded online aswell I believe)
- Take your updated metadata.json file and upload it publicly with https://gist.github.com/
- Replace the `{TOKEN_ADDRESS}`, `{NETWORK_URL}`, `{TOKEN_NAME}`, `{TOKEN_SYMBOL}` and `{METADATA_URL}` fields in main.ts

You can then run your main.ts script with ```ts-node main.ts``` assuming you have your NPM dependencies to run this typescript file.
Finally, go on the Solana Explorer and check if everything worked correctly. Check it even if you get errors in your terminal.

#### This README provides a structured and readable format for the Solana wallet and token commands you specified. 
