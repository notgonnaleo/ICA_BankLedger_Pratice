## Level 3 — Scheduled Payments & Cashback

### SCHEDULE_PAYMENT(account_id, target_id, amount, cashback_percent, timestamp, delay)

Schedules a transfer of amount from account_id to target_id at timestamp + delay.
After the transfer executes, cashback_percent% of amount is returned to account_id.
Returns a unique payment_id.

### GET_PAYMENT_STATUS(account_id, payment_id, timestamp)

Returns SCHEDULED if the payment is pending, PROCESSED if executed, or FAILED if the account had insufficient funds at execution time.
Scheduled payments execute automatically when any operation with a timestamp >= scheduled_time is processed.