Banck account manager 

Creating a system that manages bank account holders ,  like transferring money , withdraw ,deposit and also detect suspicious activity or fraud.

REQUIREMENTS
Bank account holders
Money transfer
Money withdrawal
Money transaction limit
Money into the  account

1.USER Profile
Each User must has  a unique account number and username and password (e,g ALICE, BOB)
User account balance is stored and updated 
Previous transaction records are maintained

2.Transaction Validation
before depositing ,withdrawing or transferring money user have to check first the account before	 validating a transaction

3.Available balance
The system display the users current  balance
For withdrawal and transfers available balance must be greater than or equal to the amount being moved.

e.g If Alice has R200 and tries to withdraw R400 the transaction must decline

4.Rapid Withdrawals 
System keeps track of withdrawal times.

If user tries to withdraw more than 3 times within 10 seconds , the system will detect some fraudulent transactions or suspicious transactions and block the transaction.


5.Check for Unusual Spending

The system monitors users average  transaction amount 
If ALICE normally transfers 200 and suddenly wants to transfer 1000
The system will recognize this very different from her normal behavior and flag/blog it according to the system rule 

6.Daily limit
The daily spending limit is set to R5000
If the user attempts to spend more than R5000 in a day the transaction will decline 
User can not make more than 3 transactions that exceed the daily amount  which is R5000

7.Deposit 
Deposited funds added  to the available balance
Transaction history is updated with each deposit.



