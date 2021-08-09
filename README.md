# Token Creation
Create a contract that creates tokens from OpenZeppelin Soliditycontract. This crowdsale contract will manage the entire process, allowing users to send ETH and get back PUP (PupperCoin).
This contract will mint the tokens automatically and distribute them to buyers in one transaction.
It will need to inherit Crowdsale, CappedCrowdsale, TimedCrowdsale, RefundableCrowdsale, and MintedCrowdsale.

## Crowdsale

You will need to provide parameters for all of the features of your crowdsale, such as the name, symbol, wallet for fundraising, goal, etc. Feel free to configure these parameters to your liking.
You can hardcode a rate of 1, to maintain parity with Ether units (1 TKN per Ether, or 1 TKNbit per wei). If you'd like to customize your crowdsale rate, follow the Crowdsale Rate calculator on OpenZeppelin's documentation. Essentially, a token (TKN) can be divided into TKNbits just like Ether can be divided into wei. When using a rate of 1, just like 1000000000000000000 wei is equal to 1 Ether, 1000000000000000000 TKNbits is equal to 1 TKN.
Since RefundablePostDeliveryCrowdsale inherits the RefundableCrowdsale contract, which requires a goal parameter, you must call the RefundableCrowdsale constructor from your PupperCoinCrowdsale constructor as well as the others. RefundablePostDeliveryCrowdsale does not have its own constructor, so just use the RefundableCrowdsale constructor that it inherits.
If you forget to call the RefundableCrowdsale constructor, the RefundablePostDeliveryCrowdsale will fail since it relies on it (it inherits from RefundableCrowdsale), and does not have its own constructor.
When passing the open and close times, use now and now + 24 weeks to set the times properly from your PupperCoinCrowdsaleDeployer contract.

![image](https://user-images.githubusercontent.com/79224741/128788218-75575011-4fe1-49d1-bcb1-6182ee07670e.png)



![image](https://user-images.githubusercontent.com/79224741/128788292-78888427-636d-4db9-99d0-2150d498f9da.png)



![image](https://user-images.githubusercontent.com/79224741/128788335-ae04277c-aa62-47b8-a683-154b0a0be67c.png)

## Compiler detail
![image](https://user-images.githubusercontent.com/79224741/128788449-cdabd77a-594f-478c-8b5f-0e7e1fbcac8b.png)



## PupperCoin Contract Creation
You will need to simply use a standard ERC20Mintable and ERC20Detailed contract, hardcoding 18 as the decimals parameter, and leaving the initial_supply parameter alone.
You don't need to hardcode the decimals, however since most use-cases match Ethereum's default, you may do so.
Simply fill in the PupperCoin.sol file with this starter code, which contains the complete contract you'll need to work with in the Crowdsale.


![image](https://user-images.githubusercontent.com/79224741/128788388-ffeb4e45-8c66-4709-80a1-ee0bc91fc515.png)
