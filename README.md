Overview -> This project assigns a credit score (0 to 1000) to wallets interacting with the Aave V2 protocol on the Polygon network. 
            The score reflects how responsibly and reliably each wallet interacts with DeFi functionalities like deposits, borrows, repays, and more.

Data -> We use raw transaction data (~100K entries) in JSON format, where each entry corresponds to a transaction made by a wallet. Each transaction includes fields like:
        - userWallet
        - action (deposit, borrow, repay, redeemunderlying, liquidationcall)
        - amount, assetPriceUSD
        - timestamp

Feature Engineering -> We group transactions by wallet and generate the following features:
        Feature                            Description
        num_transactions                   Total number of transactions
        num_deposit                        Count of deposit actions
        num_borrow                         Count of borrow actions
        num_repay                          Count of repay actions
        num_liquidationcall                Count of liquidation actions
        total_deposit_usd                  Total deposit value in USD
        total_borrow_usd                   Total borrow value in USD
        total_repay_usd                    Total repaid value in USD
        deposit_to_borrow_ratio            Ratio of deposit to borrow value
        repay_to_borrow_ratio              Ratio of repaid to borrowed value
        avg_tx_per_day                     Activeness of the wallet over its lifespan

Scoring Logic -> A rule-based scoring model is used with the following steps:
   1.Normalize selected features to range [0, 1]
   2.Assign weights to features:
      - total_deposit_usd: 20%
      - total_borrow_usd: 10%
      - total_repay_usd: 20%
      - deposit_to_borrow_ratio: 15%
      - repay_to_borrow_ratio: 25%
      - avg_tx_per_day: 10%
   3.Apply penalty of 50% to wallets with any liquidation
   4.Scale the final weighted score to a 0–1000 range

Output -> The final output is saved in a file called wallet_credit_scores.csv.
