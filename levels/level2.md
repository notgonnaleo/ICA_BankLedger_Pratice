## Level 2 — Top Spenders & History

### TOP_SPENDERS(n)

Returns the top n accounts ranked by total outgoing volume (sum of all transfers out), descending.
Ties broken by account id ascending.
Format each entry as account_id(total_outgoing).

### TRANSACTION_HISTORY(account_id)

Returns a chronological list of all transactions for the account.
Each entry includes: timestamp, type (deposit / transfer_in / transfer_out), amount, and balance after the transaction.

