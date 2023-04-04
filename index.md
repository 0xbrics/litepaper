# 0xBRICS : An Algorithmic, Multi-collateral Stablecoin Protocol

## Introduction
0xBRICS is a simplified algorithmic stablecoin protocol inspired by MakerDAO, designed to create a new currency pegged to the value of the upcoming BRICS currency. This litepaper outlines the protocol, associated mathematical formulae, and the reasoning behind the design choices, with constraints and requirements in mind.

## Protocol Overview
0xBRICS is an Ethereum-based protocol that relies on smart contracts and on-chain oracles. It maintains a 1:1 peg between 0xBRICS tokens and the upcoming $BRICS currency, which is initially assumed to be equivalent to the value of 1 gram of Gold. The protocol is fully collateralized by ETH or WBTC and generates revenue through liquidations and other mechanisms, ensuring a minimum profit of 1%.


### Simplified MakerDAO-inspired Design:

To simplify the protocol, we focus on core elements: collateralized debt positions (CDPs), on-chain oracles, and liquidation mechanisms. Advanced features and governance elements are excluded for simplicity.


### On-chain Oracles

0xBRICS uses on-chain oracles to provide reliable, tamper-proof data about the price of off-chain assets (BRICS, ETH, WBTC). Oracles are incentivized to report accurate data, ensuring the protocol's stability.


### 0xBRICS and the BRICS Currency Peg

The value of 1 0xBRICS token is pegged to the value of 1 BRICS, which we initially assume to be equal to 1 gram of Gold. Users can create 0xBRICS tokens by depositing ETH or WBTC as collateral into the protocol and taking out a loan in 0xBRICS. The collateralization ratio must be greater than a specified minimum (e.g., 150%) to ensure over-collateralization.


### Collateral and Liquidation

If the value of collateral (ETH/WBTC) falls below the minimum required collateralization ratio, the protocol triggers a liquidation process. The collateral is auctioned off to repay the debt, and a liquidation penalty is applied (e.g., 5%). This penalty is distributed to the protocol's stakeholders, contributing to the desired 1% profit.


### Profit Generation

The protocol generates revenue through liquidation penalties and stability fees. Stability fees are charged to users who take out loans in 0xBRICS and are paid when the loans are repaid. The fees are calculated as an annual percentage rate (e.g., 2%) and contribute to the minimum 1% profit for the protocol.


### Additional Concepts


#### Emergency Shutdown

In case of a black swan event or a severe market disruption, the protocol allows for an emergency shutdown, halting new loans and liquidations. This ensures the integrity of the system and protects users' funds.


#### Collateral Auctions

Collateral auctions are used to sell off liquidated collateral, ensuring a fair market value and maintaining protocol solvency.


#### Interest Rate Policy

The protocol uses an interest rate policy to maintain the peg between 0xBRICS and BRICS. It adjusts stability fees based on market demand, helping to keep the peg intact.


## Key Concepts

These following concepts and associated formulae maintain the 0xBRICS peg to the BRICS currency, even during a global currency crisis. The protocol constantly monitors the collateral ratio and exchange rates, triggering liquidations if necessary and adjusting interest rates to maintain stability. The 125% collateral ratio provides a sufficient buffer against rapid fluctuations in asset prices, ensuring that the 0xBRICS stablecoin remains pegged to the value of the BRICS currency. Here are the key mathematical formulas used in the 0xBRICS protocol:


### Collateral Ratio (CR)

`CR = (Collateral Value in BRICS) / (Debt in 0xBRICS)`

To maintain a collateral ratio of 125%, the protocol ensures that CR >= 1.25


### Collateral Value (CV)

`CV = (Collateral Amount in ETH/WBTC) * (ETH/WBTC to BRICS Exchange Rate)`


### Debt Value (DV)

`DV = (Loan Amount in 0xBRICS) * (0xBRICS to BRICS Exchange Rate)`


### Liquidation Price (LP)

`LP = (Loan Amount in 0xBRICS) / (Collateral Amount in ETH/WBTC * 1.25)`

The liquidation price is the ETH/WBTC to BRICS exchange rate at which the collateral ratio would fall to 125%, triggering a liquidation.


### Liquidation Penalty (LQ_Penalty)

`LQ_Penalty = Liquidation Penalty Rate * Collateral Value`

The liquidation penalty rate will be set to 5%.


### Stability Fee (SF)

`SF = Stability Fee Annual Percentage Rate * Loan Amount in 0xBRICS * (Loan Duration in Days / 365)`


### Interest Rate Adjustment (IRA)

The protocol uses an interest rate policy to adjust the stability fee based on market demand for 0xBRICS. A simple formula for this adjustment could be:

`IRA = Target Collateral Ratio - Current Collateral Ratio`

If the current collateral ratio is lower than the target ratio (125%), the stability fee increases. Conversely, if the current collateral ratio is higher than the target ratio, the stability fee decreases.


## Protocol Dependencies

The 0xBRICS protocol depends on several key external parties. By interacting with these external parties, the 0xBRICS protocol can maintain stability, ensure solvency, and adapt to market conditions. Buyers of liquidated collateral, keepers, and governance participants are incentivized through rewards and potential profit opportunities to contribute to the protocol's proper functioning.


### On-chain Oracles

The protocol relies on on-chain oracles to provide accurate and up-to-date price data for the off-chain assets (BRICS, ETH, and WBTC). Oracles can be third-party services like Chainlink or decentralized oracle networks such as Band Protocol. They play a crucial role in maintaining the collateral ratios and triggering liquidations when necessary.


### Collateral Liquidation Buyers

During a liquidation event, collateral is auctioned off to cover the outstanding debt. Buyers can be individual traders, arbitrageurs, or institutional investors who are looking for opportunities to purchase collateral at potentially discounted prices. These buyers help maintain the protocol's solvency by providing liquidity during liquidation events.


### Users (Borrowers and Lenders)

The protocol depends on users who deposit collateral (ETH or WBTC) and take out loans in 0xBRICS. These users contribute to the demand for 0xBRICS tokens and help maintain the peg to the BRICS currency.


### Keepers

Keepers are external actors responsible for monitoring the protocol and initiating liquidations when the collateral ratio falls below the threshold. They are incentivized to perform this role by earning a portion of the liquidation penalty as a reward.


### Developers and Auditors

 The protocol depends on developers to create and maintain the smart contracts, and auditors to ensure the security and reliability of the system. Regular audits help identify potential vulnerabilities and maintain user confidence in the protocol.


### Governance Participants: 

Although the 0xBRICS protocol is designed to be simplified and does not focus on governance, it may still benefit from a decentralized governance system to make decisions about protocol upgrades, risk parameters, and other essential aspects. Governance participants could include token holders, users, and other stakeholders who are incentivized to maintain the protocol's stability and value.


## Quantitative Analysis

Here are some scenarios demonstrating how the 0xBRICS protocol would behave under various conditions


### Normal Market Conditions

* ETH to BRICS exchange rate: 0.01 ETH/BRICS
* WBTC to BRICS exchange rate: 0.00025 WBTC/BRICS
* User deposits 100 ETH as collateral
* Collateral Value (CV) = 100 ETH * 0.01 ETH/BRICS = 1000 BRICS
* Loan Amount in 0xBRICS: CV * 0.8 (80% of the collateral value) = 800 0xBRICS
* Collateral Ratio (CR) = CV / DV = 1000 / 800 = 1.25

Under normal market conditions, the user can take out an 800 0xBRICS loan against their 100 ETH collateral at a 125% collateral ratio.


### ETH Price Drop

* ETH to BRICS exchange rate drops to 0.008 ETH/BRICS
* New Collateral Value (CV) = 100 ETH * 0.008 ETH/BRICS = 800 BRICS
* Collateral Ratio (CR) = CV / DV = 800 / 800 = 1.0

The collateral ratio falls below the 1.25 threshold, triggering a liquidation. The protocol auctions off the user's collateral to cover the debt.


### BRICS Currency Appreciates

* BRICS to Gold exchange rate increases, causing 1 BRICS to be worth 1.1 grams of Gold
* 0xBRICS to BRICS exchange rate: 1 0xBRICS = 1.1 grams of Gold
* New Debt Value (DV) = 800 0xBRICS * 1.1 grams of Gold = 880 grams of Gold
* Collateral Ratio (CR) = CV / DV = 1000 / 880 = 1.136

As the BRICS currency appreciates, the collateral ratio falls below the target of 1.25. The protocol will adjust the stability fee to incentivize users to repay loans and restore the collateral ratio.


### ETH Price Increase

* ETH to BRICS exchange rate rises to 0.012 ETH/BRICS
* New Collateral Value (CV) = 100 ETH * 0.012 ETH/BRICS = 1200 BRICS
* Collateral Ratio (CR) = CV / DV = 1200 / 800 = 1.5

With the increase in ETH price, the collateral ratio rises above the target of 1.25. The protocol will lower the stability fee to encourage users to take out more loans, thus increasing the demand for 0xBRICS and maintaining the peg.


### Global Currency Crisis

* BRICS currency remains stable due to its commodity backing, with 1 BRICS still worth 1 gram of Gold
* ETH and WBTC prices become volatile
* The protocol's liquidation mechanism and interest rate adjustments help maintain the 0xBRICS peg to the BRICS currency, providing a safe haven for users during the crisis.


## Conclusion

0xBRICS is a simplified, resilient algorithmic stablecoin protocol that maintains a stable peg to the BRICS currency. By utilizing ETH and WBTC as collateral, incorporating on-chain oracles, and employing liquidation mechanisms, 0xBRICS ensures stability and generates a minimum profit of 1% for the protocol.

## Contributing

Please visit the [Github repo](https://github.com/0xbrics/litepaper) for details on how to contribute.