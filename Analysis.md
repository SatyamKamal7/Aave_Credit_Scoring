Score Distribution -> After scoring all wallets, the distribution of credit scores (0–1000) is as follows:
   Score Range         wallets          Observations
   0–100               very few          Mostly liquidated or extremely low repay ratio
   100–200             few               Risky wallets, low deposit or low repay activity
   200-400             moderate          Some repayment, but borrow-heavy and low deposit
   400-700             many              Balanced activity, partial repays, fewer liquidations
   700-900             many              Active wallets with high deposits and good repay behavior
   900-1000            top tier          Most reliable wallets, no liquidation, very high repay-to-borrow ratio

   Most wallets fell in the 400–900 range, indicating generally responsible behavior.

Characteristics of Low-Scoring Wallets (0–300)
->High number of borrow transactions
->Little or no repay activity
->Very low deposit-to-borrow ratio
->At least one liquidationcall (triggering the penalty)

Characteristics of High-Scoring Wallets (800–1000)
->Large total deposits in USD
->High repay-to-borrow ratio (> 1.0)
->Active over long periods (more than 30 days)
->No liquidation history
->Consistent deposit and repay actions

Score Insights
->Repay-to-borrow ratio is the strongest predictor of reliability
->Liquidation is the most penalized behavior (cuts score by 50%)
->Activeness (avg_tx/day) correlates positively with good credit behavior
