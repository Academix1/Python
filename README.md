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
# User Registration
print("--- User Registration ---")
name = input("Enter your name: ")  # String
phone = input("Enter your mobile number: ")  # String
while len(phone) != 10 or not phone.isdigit():  # Loop for valid phone number
    print("Invalid phone number. Please enter a 10-digit number.")
    phone = input("Enter your mobile number: ")

initial_balance = float(input("Enter your initial deposit amount: ₹"))  # Float
while initial_balance <= 0:  # Loop for valid initial deposit
    print("Initial deposit must be greater than ₹0.")
    initial_balance = float(input("Enter your initial deposit amount: ₹"))

pin = input("Set your 4-digit PIN: ")  # String
while len(pin) != 4 or not pin.isdigit():  # Loop for valid PIN
    print("Invalid PIN. It must be a 4-digit number.")
    pin = input("Set your 4-digit PIN: ")

print(f"\nRegistration Successful!")
print(f"Name: {name}, Phone: {phone}, Balance: ₹{initial_balance}, PIN: {pin}")

# Function to validate PIN
def validate_pin(saved_pin, entered_pin):
    return saved_pin == entered_pin

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

# Balance Operations with PIN Validation
print("\n--- Balance Operations ---")
entered_pin = input("Enter your PIN to validate: ")
if validate_pin(pin, entered_pin):  # Validate the PIN
    print("PIN Verified!")
    balance = initial_balance

    while True:  # Loop for multiple operations
        print("\nAvailable Operations:")
        print("1. Deposit Amount")
        print("2. Withdraw Amount")
        print("3. Exit")
        choice = input("Enter your choice (1/2/3): ")

        if choice == "1":  # Deposit Operation
            deposit_amount = float(input("Enter amount to deposit: ₹"))
            while deposit_amount <= 0:  # Validate deposit amount
                print("Deposit amount must be greater than ₹0.")
                deposit_amount = float(input("Enter amount to deposit: ₹"))
            balance = update_balance(balance, deposit_amount, "deposit")
            print(f"Balance after deposit: ₹{balance}")

        elif choice == "2":  # Withdrawal Operation
            withdraw_amount = float(input("Enter amount to withdraw: ₹"))
            while withdraw_amount <= 0:  # Validate withdrawal amount
                print("Withdrawal amount must be greater than ₹0.")
                withdraw_amount = float(input("Enter amount to withdraw: ₹"))
            balance = update_balance(balance, withdraw_amount, "withdraw")
            print(f"Balance after withdrawal: ₹{balance}")

        elif choice == "3":  # Exit
            print("Thank you for using our services. Goodbye!")
            break

        else:  # Invalid Choice
            print("Invalid choice. Please enter 1, 2, or 3.")
else:
    print("PIN Validation Failed!")



```
