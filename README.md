# Scenario
Your task is to implement a simplified version of a banking system. All operations that should be supported are listed below. Partial credit will be granted for each test passed, so press "Submit" often to run tests and receive partial credits for passed tests. Please check tests for requirements and argument types.
Example of account structure:
[bank]
    Balance
    +- acc-alice   $5000
    +- acc-bob     $2300
    +- acc-carol   $800

## Level 1 — Basic Operations

### CREATE_ACCOUNT(account_id)

Creates a new account with balance 0.
If an account with the same id already exists, throws a runtime exception.


### DEPOSIT(account_id, amount)

Deposits amount into the account. Returns the new balance.
If the account does not exist, throws a runtime exception.
If amount is not positive, throws a runtime exception.


### TRANSFER(from_id, to_id, amount)

Transfers amount from one account to another. Returns the new balance of from_id.
If either account does not exist, throws a runtime exception.
If from_id and to_id are the same, throws a runtime exception.
If from_id has insufficient funds, throws a runtime exception.




## Level 2 — Top Spenders & History

### TOP_SPENDERS(n)

Returns the top n accounts ranked by total outgoing volume (sum of all transfers out), descending.
Ties broken by account id ascending.
Format each entry as account_id(total_outgoing).


### TRANSACTION_HISTORY(account_id)

Returns a chronological list of all transactions for the account.
Each entry includes: timestamp, type (deposit / transfer_in / transfer_out), amount, and balance after the transaction.




## Level 3 — Scheduled Payments & Cashback

### SCHEDULE_PAYMENT(account_id, target_id, amount, cashback_percent, timestamp, delay)

Schedules a transfer of amount from account_id to target_id at timestamp + delay.
After the transfer executes, cashback_percent% of amount is returned to account_id.
Returns a unique payment_id.


### GET_PAYMENT_STATUS(account_id, payment_id, timestamp)

Returns SCHEDULED if the payment is pending, PROCESSED if executed, or FAILED if the account had insufficient funds at execution time.


Scheduled payments execute automatically when any operation with a timestamp >= scheduled_time is processed.


## Level 4 — Account Merging

### MERGE_ACCOUNTS(account_id_1, account_id_2)

Merges account_id_2 into account_id_1.
account_id_1 receives the combined balance of both accounts.
All future references to account_id_2 (including scheduled payments) are redirected to account_id_1.
The full transaction history of account_id_2 is appended to account_id_1's history, re-sorted chronologically.
account_id_2 no longer exists after the merge.
If either account does not exist, throws a runtime exception.
Merging an account with itself throws a runtime exception.