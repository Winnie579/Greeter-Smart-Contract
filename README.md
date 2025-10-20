# 👋🏻 Greeter Smart Contract (Base Sepolia)

A minimal Greeter smart contract built with [Foundry](https://book.getfoundry.sh/), deployed to the [Base Sepolia](https://sepolia.basescan.org/) testnet, and verified using Foundry’s native tooling. This guide walks through setup, compilation, deployment, and verification.

---

## 🛠️ Setup Instructions

### 1. Create Project Directory

```
mkdir Greeter-Smart-Contract
cd Greeter-Smart-Contract
```




### 2. Install Foundry

```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```
### 3. Initialize the Project

```
forge init
```


### 4. Environment Configuration

Create a .env file to securely store sensitive values:
```
PRIVATE_KEY=your-wallet-private-key
ETHERSCAN_API_KEY=your-basescan-api-key
RPC_URL=<https://sepolia.base.org>
```

Then load it into your shell:
`source .env`

This makes the variables available to forge create and forge verify-contract.

Always run it when:
Opening a new terminal
Modifying/adding variables to the `.env` file


### 5. Contract Code 

Replace src/Counter.sol with src/Greeting.sol and start writing your code functions and arguments


### 6. Build Your Contract

```
forge build
```

This compiles the contract and generates ABI + bytecode in out/.


### 7.🚀 Deploy to Base Sepolia

Use forge create to deploy manually:

```bash
forge create src/Greeting.sol:Greeter \
  --rpc-url $BASESCAN_RPC_URL \
  --broadcast \
  --private-key $PRIVATE_KEY \
  --constructor-args "Hello, Base Builders!" \
```
Note: --broadcast sends the transaction to the network using the provided RPC and private key.

### 8. ✅ Verify on Basescan
Once deployed, verify the contract:

```bash
forge verify-contract \
  --chain base-sepolia \
  0xYourContractAddress \
  src/Greeting.sol:Greeter \
  --verifier etherscan \
  --verifier-url https://api-sepolia.basescan.org/api \
  --etherscan-api-key $ETHERSCAN_API_KEY \
  --constructor-args $(cast abi-encode "constructor(string)" "Hello, Base builders!")

```
Make sure:

* The contract address is correct

* The contract name matches exactly

* Your .env is sourced before running this



### View on Basescan

Contract Address: 0xYourContractAddress

<https://sepolia.basescan.org/address/YourContractAddress>

Verified on: [Basescan](https://sepolia.basescan.org/)


