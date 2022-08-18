1- <!-- for get download in operating system --> 

https://geth.ethereum.org/docs/install-and-build/installing-geth#install-on-windows

2- <!-- make directly and navigate to it -->

md privatechain 

3- <!-- to check if geth is present -->

geth

 4- <!-- make 2 accounts using the below command -->

geth account new

5- <!-- create a  file named as genesis-block.json -->

{
  "config": {
    "chainId": 15,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "ethash": {}
  },
  "difficulty": "1",
  "gasLimit": "8000000",
  "alloc": {},
}

6- <!-- Next, initialize Geth  -->

geth --datadir . init genesis-block.json

7- <!-- Notice how the last line says “Successfully wrote genesis state”, this simply means we’ve successfully created our private blockchain, we can go ahead and get it started by running: -->

geth --allow-insecure-unlock --datadir . --keystore ~/Library/ethereum/keystore --networkid 4568 --http --http.addr '0.0.0.0' --http.corsdomain "*" --http.port 8502 --http.api 'personal,eth,net,web3,txpool,miner' --mine --miner.etherbase=YOUR_ETHEREUM_ADDRESS_HERE


8- <!-- Note: running the above command starts an interactive session that continues to print stuff to the console, thereby not allowing us to type in new commands. Leave it running that way and open a new console, then navigate into the private-blockchain directory and type in this command to begin interacting with our private blockchain: -->

geth attach geth.ipc
<!-- This will load the web3 module into the console and expose a ton of functions.  -->

9- <!-- eth.getBalance(eth.accounts[index]) index=0 for account 1 -->
eth.getBalance(eth.accounts[0]) 

10- <!-- To begin mining on our private blockchain, we simply need to run: -->
miner.start()

11- <!-- Allow it to run for a while and then stop the process with: -->
miner.stop()

12- <!-- Notice that you’ve been rewarded with some tokens (depending on how long you left it running) for mining new blocks -->

eth.getBalance(eth.accounts[index])   
 <!-- index=0 for account 1  it check balance of account-->

13- <!--for  Sending Tokens (Wei) from one account to another -->

<!-- unlock account from which ether have to send -->
personal.unlockAccount(eth.accounts[index])   

14- <!-- transection send from account 1 ---> 2 -->

eth.sendTransaction({from: eth.accounts[0], to: eth.accounts[1], value: 500000})

15- <!-- transection done but not mined. For mining,  u have to run start mining comand and after a couple of seconds stop command run -->

miner.start()
miner.stop()

16 - <!--check balance after mining -->
eth.getBalance(eth.accounts[1])


reference:  https://mirror.xyz/arinze.eth/82tNmOWqsGG44C7r8RwqHSEOBdfsRRpYLGpSqRY05_M