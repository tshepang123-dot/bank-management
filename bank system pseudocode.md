BEGIN

  // Step 1: Create User Profile
  FOR each new user
    ASSIGN unique account_number, username, password
    SET balance = initial deposit
    INITIALIZE transaction_history = empty list
  END FOR

  // Step 2: Validate Transactions
  FUNCTION validate_transaction(user, transaction_type, amount, target_account)
    IF user account not found OR password invalid
       DISPLAY "Invalid account or authentication failed"
       RETURN false
    END IF
    RETURN true
  END FUNCTION

  // Step 3: Check Available Balance
  FUNCTION check_balance(user)
    DISPLAY user.balance
  END FUNCTION

  FUNCTION withdraw(user, amount)
    IF amount <= user.balance
       user.balance = user.balance - amount
       UPDATE transaction_history
       DISPLAY "Withdrawal successful"
    ELSE
       DISPLAY "Insufficient funds"
    END IF
  END FUNCTION

  FUNCTION transfer(user, target_account, amount)
    IF amount <= user.balance
       user.balance = user.balance - amount
       target_account.balance = target_account.balance + amount
       UPDATE transaction_history
       DISPLAY "Transfer successful"
    ELSE
       DISPLAY "Insufficient funds"
    END IF
  END FUNCTION

  // Step 4: Monitor Rapid Withdrawals
  FUNCTION monitor_withdrawals(user)
    IF user.withdrawals_in_last_10_seconds > 3
       FLAG transaction as suspicious
       BLOCK transaction
       DISPLAY "Suspicious activity detected"
    END IF
  END FUNCTION

  // Step 5: Detect Unusual Spending
  FUNCTION detect_unusual_spending(user, amount)
    CALCULATE average_transaction = mean(user.transaction_history)
    IF amount > (average_transaction * 3)   // threshold rule
       FLAG transaction as unusual
       DISPLAY "Transaction flagged as unusual"
    END IF
  END FUNCTION

  // Step 6: Enforce Daily Limit
  FUNCTION enforce_daily_limit(user, amount)
    IF user.daily_total + amount > 5000
       DISPLAY "Daily limit exceeded"
       DECLINE transaction
    ELSE
       user.daily_total = user.daily_total + amount
       ALLOW transaction
    END IF
  END FUNCTION

  // Step 7: Handle Deposits
  FUNCTION deposit(user, amount)
    user.balance = user.balance + amount
    UPDATE transaction_history
    DISPLAY "Deposit successful"
  END FUNCTION

END
