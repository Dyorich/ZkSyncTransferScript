# ZkSync_Transfer_Script
This script demonstrates how to use ZkSync's JavaScript library to send ETH (Ethereum) from your ZkSync wallet to a recipient address. 
const { ethers } = require("ethers");
const { Wallet } = require("zksync");

// Set up your ZkSync provider and wallet
const zkSyncProvider = ethers.getDefaultProvider("rinkeby");
const privateKey = "your-private-key";
const zkSyncWallet = await Wallet.fromEthSigner(new ethers.Wallet(privateKey), zkSyncProvider);

// Specify the recipient address and amount
const recipientAddress = "0x1234567890abcdef1234567890abcdef12345678";
const amount = ethers.utils.parseEther("0.1");

// Send the transaction
const transfer = await zkSyncWallet.syncTransfer({
  to: recipientAddress,
  token: "ETH",
  amount: amount,
});

// Wait for the transaction to be confirmed
const receipt = await transfer.awaitReceipt();

console.log("Transaction hash:", receipt.transactionHash);
console.log("Transfer complete!");
