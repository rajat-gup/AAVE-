// this code use land data for broowser
<!DOCTYPE html>
<html lang="en">

<head>
    <script type="text/javascript" src="node_modules/web3/dist/web3.min.js"></script>
    <title>My Token Faucet</title>
</head>

<body>
    <h2>This is Daphnis Project</h2>
    <br />
    <h3>Enter amount of tokens to claim:</h3>

    <form id="tokenClaim">
        <input id="input" type="text" />
        <input id="submitBtn" type="submit" value="Request" />
    </form>

    <script>


        // Check for a Web3 provider network provider 

        var web3 = new Web3(new Web3.providers.HttpProvider('https://mainnet.infura.io/v3/b8d33a1adfae4e60a75a93c46f01f068'));
        console.log(web3);
        // intract mainnet to web3 js
        var contractAdd = "0x4da27a545c0c5B758a6BA100e3a049001de870f5"; // Contract address
        var abi = [{ "anonymous": false, "inputs": [{ "indexed": false, "internalType": "address", "name": "previousAdmin", "type": "address" }, { "indexed": false, "internalType": "address", "name": "newAdmin", "type": "address" }], "name": "AdminChanged", "type": "event" }, { "anonymous": false, "inputs": [{ "indexed": true, "internalType": "address", "name": "implementation", "type": "address" }], "name": "Upgraded", "type": "event" }, { "stateMutability": "payable", "type": "fallback" }, { "inputs": [], "name": "admin", "outputs": [{ "internalType": "address", "name": "", "type": "address" }], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [{ "internalType": "address", "name": "newAdmin", "type": "address" }], "name": "changeAdmin", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [], "name": "implementation", "outputs": [{ "internalType": "address", "name": "", "type": "address" }], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [{ "internalType": "address", "name": "_logic", "type": "address" }, { "internalType": "address", "name": "_admin", "type": "address" }, { "internalType": "bytes", "name": "_data", "type": "bytes" }], "name": "initialize", "outputs": [], "stateMutability": "payable", "type": "function" }, { "inputs": [{ "internalType": "address", "name": "_logic", "type": "address" }, { "internalType": "bytes", "name": "_data", "type": "bytes" }], "name": "initialize", "outputs": [], "stateMutability": "payable", "type": "function" }, { "inputs": [{ "internalType": "address", "name": "newImplementation", "type": "address" }], "name": "upgradeTo", "outputs": [], "stateMutability": "nonpayable", "type": "function" }, { "inputs": [{ "internalType": "address", "name": "newImplementation", "type": "address" }, { "internalType": "bytes", "name": "data", "type": "bytes" }], "name": "upgradeToAndCall", "outputs": [], "stateMutability": "payable", "type": "function" }];
      
      
        var contract = new web3.eth.Contract(abi, contractAdd);
        console.log(contract);
        
        // call functin and fatch data
        const balance = async () => {
            console.log("cheack function======>");

            web3.eth.getBlock('latest').then(console.log)
            //var totalSupply = await web3.eth.totalSupply();
            //console.log("totalSupply", totalSupply.toString());

            const balance = await web3.eth.getBalance('0xd3db7913a622B28a9b647CaC83226d2c3C9FE55a');
            console.log("balance", balance);

            //const stakerRewordsToClaim = await contract.methods.stakerRewardsToClaim("0xBa62c32613DD32CBAC89f502Dc7eDb05ea1f911f")
            //console.log(stakerRewordsToClaim);

        }
        balance();

    </script>
</body>

</html>
