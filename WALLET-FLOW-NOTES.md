# LineGuard Wallet Flow (Cashfree Paused)

- Cashfree checkout and its API routes have been removed/paused. No live payment gateway is configured.
- The accused can enter the amount they say they paid directly to the reporter and submit a public apology. This creates an **awaiting confirmation** record; it does not itself credit the wallet.
- The reporter must confirm that the money actually arrived. Only then is the report marked resolved and the amount counted in the reporter's Profile wallet.
- The Profile shows confirmed wallet balance and a ₹100 minimum redemption threshold. Actual withdrawals/redemptions are intentionally not enabled until a payout provider, identity checks, and secure server-side ledger are implemented.
- This source currently persists demo app data in device-local AsyncStorage. It is not a production multi-user wallet or a secure financial ledger: separate devices/accounts will not share/verify these records. Do not treat displayed balances as real funds until a shared backend and audited transaction flow are built.
