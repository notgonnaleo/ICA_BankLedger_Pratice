## Level 4 — Account Merging

### MERGE_ACCOUNTS(account_id_1, account_id_2)

Merges account_id_2 into account_id_1.
account_id_1 receives the combined balance of both accounts.
All future references to account_id_2 (including scheduled payments) are redirected to account_id_1.
The full transaction history of account_id_2 is appended to account_id_1's history, re-sorted chronologically.
account_id_2 no longer exists after the merge.
If either account does not exist, throws a runtime exception.
Merging an account with itself throws a runtime exception.