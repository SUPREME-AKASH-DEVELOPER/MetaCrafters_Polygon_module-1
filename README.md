# MetaCrafters_Polygon_module-1
# Project Title: NFT Bridge from Ethereum to Polygon Using Polygon Bridge

**Author:** Akash  
**Email:** akashlakhwan2329@gmail.com

## Project Overview

This project is part of the Polygon Proof of Stake Challenge, where the objective is to migrate an NFT collection from the Ethereum blockchain to the Polygon network using the Polygon Bridge. The project involves generating NFTs using AI tools, storing the images on IPFS via Pinata, deploying smart contracts on the Ethereum Goerli Testnet, and finally bridging the NFTs to the Polygon Mumbai network.

## Description

In this project, we demonstrate the process of migrating NFTs from the Ethereum network to the Polygon network, utilizing the Polygon Bridge for cross-chain asset transfers. This is particularly useful given the deprecation of Goerli and Mumbai testnets, making this project a practical example for current blockchain applications.

The contract `NFTCollection.sol` leverages the ERC721A standard, which is ideal for batch minting multiple NFTs at once. Below is the core functionality:

```solidity
function batchMintNFT(string[] memory nftURLs, string[] memory prompts) public onlyOwner {
    require(nftURLs.length == prompts.length, "Mismatched arrays length");
    uint256 startTokenId = counter;
    uint256 numberOfTokens = nftURLs.length;

    _safeMint(owner(), numberOfTokens);

    for (uint256 i = 0; i < numberOfTokens; i++) {
        _tokenURIs[startTokenId + i] = nftURLs[i];
        _prompts[startTokenId + i] = prompts[i];
    }

    counter += numberOfTokens;
}
```

## Tools Used

- **Hardhat:** For writing, deploying, and testing smart contracts.
- **Pinata.cloud:** For storing NFT images on IPFS.
- **FxPortal Bridge:** For transferring NFTs from Ethereum to Polygon.
- **DALLE-2/MidJourney:** For generating unique NFT images.

## Installation

To run this project locally, follow these steps:

1. **Fork and Clone the Repository:**  
   Fork this repository and clone it to your local machine.

2. **Install Dependencies:**  
   Ensure Node.js is installed. Then, run:
   ```bash
   npm install
   ```

3. **Setup .env File:**  
   Create a `.env` file and add your RPC URLs and wallet private key.

## Execution

Follow these commands to deploy and manage your NFTs:

1. **Compile the Smart Contract:**
   ```bash
   npx hardhat compile
   ```

2. **Deploy the Contract on Goerli:**
   ```bash
   npx hardhat run scripts/deploy.js --network goerli
   ```

3. **Batch Mint NFTs on Goerli:**
   ```bash
   npx hardhat run scripts/batchMint.js --network goerli
   ```

4. **Approve and Deposit NFTs for Bridging:**
   ```bash
   npx hardhat run scripts/approveDeposit.js --network goerli
   ```

5. **Verify NFT Balance on Polygon Mumbai:**
   After waiting for the bridging process to complete, run:
   ```bash
   npx hardhat run scripts/getBalance.js --network mumbai
   ```

## Help

**Faucets:**  
Ensure you have sufficient testnet ETH/MATIC for transactions.  
- [Sepolia Faucet](https://cloud.google.com/application/web3/faucet/ethereum/sepolia)
- [Polygon Faucet](https://faucet.polygon.technology/)

For more details on Avalanche, visit [Avalanche Documentation](https://docs.avax.network/).

## Screenshots

Since the process of updating on the Amoy chain takes around 40-50 minutes, I’ve included screenshots of the transaction on Etherscan as proof of successful migration. You can find these in the repository.

- [Etherscan Transaction](https://sepolia.etherscan.io/tx/0x1ae1db069c677f0dd1eea06e9ea13ae240b40977894026d1193b2778dc854936)

![image](https://github.com/user-attachments/assets/af384570-d998-44cf-9707-5a41cda77877)
![image](https://github.com/user-attachments/assets/d7135205-47ee-480b-82d3-d1ee843045c2)

## Loom Link: 
https://www.loom.com/share/791f6b6d4cb14392bcdfc593e3dbcc1e?t=2&sid=6c7e8167-e808-4953-a533-70dc02b5c31a

