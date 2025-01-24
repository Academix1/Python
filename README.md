# Python Day4 Code

## Concept:Functions

### Python DayWise

```python

# Function to validate PIN
def validate_pin(pin, entered_pin):
    return pin == entered_pin

# Function to update balance
def update_balance(current_balance, transaction_amount, transaction_type):
    if transaction_type == "deposit":
        return current_balance + transaction_amount
    elif transaction_type == "withdraw":
        if current_balance >= transaction_amount:
            return current_balance - transaction_amount
        else:
            print("Insufficient balance!")
            return current_balance
    else:
        print("Invalid transaction type.")
        return current_balance

# Example usage
pin = input("Set your 4-digit PIN: ")
entered_pin = input("Enter your PIN to validate: ")
if validate_pin(pin, entered_pin):
    print("PIN Verified!")
    balance = float(input("Enter your current balance: ₹"))
    amount = float(input("Enter transaction amount: ₹"))
    transaction_type = input("Enter transaction type (deposit/withdraw): ").lower()
    balance = update_balance(balance, amount, transaction_type)
    print(f"Updated Balance: ₹{balance}")
else:
    print("PIN Validation Failed!")


```

### Python Main Code
```python
# Get user name
name = input("Enter Name: ")

# Get and validate initial balance
initial_balance = float(input("Enter Your Balance: "))
while initial_balance <= 0:
    print("Balance Should be greater than 0.")
    initial_balance = float(input("Enter Your Balance: "))

# Set and validate PIN
pin = input("Set Your PIN (4-digit): ")
while len(pin) != 4 or not pin.isdigit():
    print("Invalid PIN. Enter a 4-digit numeric PIN.")
    pin = input("Set Your PIN (4-digit): ")

# Function to validate the entered PIN
def validate_pin(stored_pin, entered_pin):
    return stored_pin == entered_pin

# Function to handle deposit
def deposit(balance, damount):
    balance += damount
    return balance

# Function to handle withdrawal
def withdraw(balance, wamount):
    while wamount > balance:
        print("Withdrawal amount should not exceed the current balance.")
        wamount = float(input("Enter a valid Withdrawal Amount: "))
    balance -= wamount
    return balance

# Main Program
while True:
    re_rentered_pin=input("Enter Your PIN: ")
    if validate_pin(pin, re_rentered_pin):
        print(f"Welcome {name}!")
        while True:
            print("\nOptions:")
            print("1. Deposit")
            print("2. Withdraw")
            print("3. Exit")
            choice = input("Enter your choice: ")

            if choice == "1":
                deposit_amount = float(input("Enter the amount to deposit: "))
                initial_balance = deposit(initial_balance, deposit_amount)
                print(f"Your current balance is: {initial_balance}")
            elif choice == "2":
                withdrawal_amount = float(input("Enter the amount to withdraw: "))
                initial_balance = withdraw(initial_balance, withdrawal_amount)
                print(f"Your current balance is: {initial_balance}")
            elif choice == "3":
                print("Goodbye!")
                break
            else:
                print("Invalid choice. Please try again.")
    else:
        print("Incorrect PIN. Please try again.")


```
