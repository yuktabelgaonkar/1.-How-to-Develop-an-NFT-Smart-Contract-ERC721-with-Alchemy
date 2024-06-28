# How-to-Develop-an-NFT-Smart-Contract-ERC721-with-Alchemy
Learn to develop an ERC721 NFT smart contract using Alchemy. Utilize Solidity, Remix IDE, and OpenZeppelin for secure and efficient development on the Ethereum blockchain, testing on Sepolia testnet via Alchemy for deployment and testing.

Here's a step-by-step guide on how to develop and deploy an ERC721 (NFT) smart contract using Alchemy, OpenZeppelin, Remix, and the Ethereum Sepolia testnet. This tutorial is designed for beginners and includes all the necessary updates as of now.

Step 1: Setting Up Your Development Environment 
1.1 Create a Free Alchemy Account
Sign Up: Go to Alchemy and sign up for a free account.
Create an App:
Select the Ethereum ecosystem.
Give your app a name and select the Sepolia testnet.
Create the app.
1.2 Install MetaMask
Download MetaMask: If you don't have MetaMask, download it from here.
Set Up Wallet: Create a new wallet and securely store your seed phrase.
Connect to Alchemy:
Open MetaMask.
Click on the network dropdown and select "Add Network".
Enter the following details:
Network Name: Alchemy Sepolia
New RPC URL: The HTTP URL from your Alchemy app
Chain ID: 11155111
Currency Symbol: Sepolia ETH
Block Explorer URL: https://sepolia.etherscan.io/
Save and switch to the Alchemy Sepolia network.

Step 2: Writing the Smart Contract
2.1 OpenZeppelin Contract Wizard
Visit OpenZeppelin Wizard: Go to OpenZeppelin Contract Wizard.
Select ERC721:
Choose ERC721.
Name your token and symbol.
Select Features:
Enable the following:
Mintable
Autoincrement IDs
Enumerable
URI Storage
Leave others unchecked.
2.2 Generate and Copy Code
Generate Code: The wizard will generate the smart contract code.
Copy Code: Copy the generated code.
2.3 Modify the Code in Remix
Open Remix: Go to Remix IDE.
Create a New File: Name it NFT.sol and paste the copied code.
Modify the Contract:
Add the following imports at the top:
solidity
Copy code
import "@openzeppelin/contracts/utils/Counters.sol";
Initialize Counters in the contract:
solidity
Copy code
Counters.Counter private _tokenIdCounter;
uint256 MAX_SUPPLY = 10000;
Modify the safeMint function:
solidity
Copy code
function safeMint(address to, string memory uri) public {
    require(_tokenIdCounter.current() < MAX_SUPPLY, "I'm sorry we reached the cap");
    uint256 tokenId = _tokenIdCounter.current();
    _tokenIdCounter.increment();
    _safeMint(to, tokenId);
    _setTokenURI(tokenId, uri);
}

Step 3: Deploying the Smart Contract
3.1 Compile the Contract
Compile: Click on the Solidity compiler and compile NFT.sol.
3.2 Deploy the Contract
Deploy:
Click on "Deploy & Run Transactions".
Select "Injected Web3" as the environment.
Ensure MetaMask is connected to Alchemy Sepolia.
Select the contract and click "Deploy".
Confirm the transaction in MetaMask.

Step 4: Minting NFTs
4.1 Get Sepolia Test ETH
Sepolia Faucet: Go to Sepolia Faucet, enter your wallet address, and get some Sepolia ETH.
4.2 Mint NFT
Metadata:

Create a JSON file for your NFT metadata:
json
Copy code
{
  "description": "Your NFT Description",
  "external_url": "Your URL",
  "image": "IPFS URL of your image",
  "name": "Your NFT Name",
  "attributes": [
    {
      "trait_type": "Attribute Type",
      "value": "Attribute Value"
    }
  ]
}
Upload the image and metadata to Filebase or any IPFS service.
Get the IPFS URLs.
Mint Using Remix:

Go to Remix.
Use the safeMint function:
Address: Your MetaMask address.
URI: IPFS URL of the metadata.
Confirm the transaction in MetaMask.

Step 5: Visualize on OpenSea
OpenSea Testnet: Go to OpenSea Testnet.
Login: Connect your MetaMask wallet.
View NFT: Your NFT should appear in your profile. If not, click on "Refresh Metadata".
Congratulations! You have successfully created, deployed, and minted an NFT smart contract on the Sepolia testnet.
