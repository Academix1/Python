# Python Day5 Code
## Arrays
### Python DayWise

```python
# List to store multiple accounts
accounts = []

# Add a new account
name = input("Enter your name: ")
phone = input("Enter your mobile number: ")
try:
    balance = float(input("Enter your initial deposit amount: ₹"))
except ValueError:
    balance = 0.0
    print("Invalid input for balance. Setting it to ₹0.")
pin = input("Set your 4-digit PIN: ")

# Add to the accounts list
accounts.append({"name": name, "phone": phone, "balance": balance, "pin": pin})
print("Account successfully created!")

# Access and update account
for account in accounts:
    if account["phone"] == phone:
        print(f"Welcome, {account['name']}! Your balance is ₹{account['balance']}.")
        new_balance = account["balance"] + 500  # Example deposit
        account["balance"] = new_balance
        print(f"After deposit, your balance is ₹{account['balance']}.")



```

### Python Main Code
```python
# List to store multiple accounts
accounts = []

# Function to validate PIN
def validate_pin(account, entered_pin):
    return account["pin"] == entered_pin

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

# Function to create a new account
def create_account():
    print("\n--- Account Registration ---")
    name = input("Enter your name: ")
    phone = input("Enter your mobile number: ")
    while len(phone) != 10 or not phone.isdigit():
        print("Invalid phone number. Please enter a 10-digit number.")
        phone = input("Enter your mobile number: ")
    
    balance = float(input("Enter your initial deposit amount: ₹"))
    while balance <= 0:
        print("Initial deposit must be greater than ₹0.")
        balance = float(input("Enter your initial deposit amount: ₹"))
    
    pin = input("Set your 4-digit PIN: ")
    while len(pin) != 4 or not pin.isdigit():
        print("Invalid PIN. It must be a 4-digit number.")
        pin = input("Set your 4-digit PIN: ")
    
    accounts.append({"name": name, "phone": phone, "balance": balance, "pin": pin})
    print(f"\nAccount successfully created for {name}!")

# Function to access an account and perform operations
def access_account():
    phone = input("Enter your registered mobile number: ")
    account = next((acc for acc in accounts if acc["phone"] == phone), None)

    if account:
        entered_pin = input("Enter your 4-digit PIN: ")
        if validate_pin(account, entered_pin):
            print(f"\nWelcome, {account['name']}! Your current balance is ₹{account['balance']}.")

            while True:
                print("\nAvailable Operations:")
                print("1. Deposit Amount")
                print("2. Withdraw Amount")
                print("3. View Balance")
                print("4. Exit")
                choice = input("Enter your choice (1/2/3/4): ")

                if choice == "1":  # Deposit Operation
                    deposit_amount = float(input("Enter amount to deposit: ₹"))
                    while deposit_amount <= 0:
                        print("Deposit amount must be greater than ₹0.")
                        deposit_amount = float(input("Enter amount to deposit: ₹"))
                    account["balance"] = update_balance(account["balance"], deposit_amount, "deposit")
                    print(f"After deposit, your balance is ₹{account['balance']}.")

                elif choice == "2":  # Withdrawal Operation
                    withdraw_amount = float(input("Enter amount to withdraw: ₹"))
                    while withdraw_amount <= 0:
                        print("Withdrawal amount must be greater than ₹0.")
                        withdraw_amount = float(input("Enter amount to withdraw: ₹"))
                    account["balance"] = update_balance(account["balance"], withdraw_amount, "withdraw")
                    print(f"After withdrawal, your balance is ₹{account['balance']}.")

                elif choice == "3":  # View Balance
                    print(f"Your current balance is ₹{account['balance']}.")

                elif choice == "4":  # Exit
                    print("Thank you for using our services. Goodbye!")
                    break

                else:  # Invalid Choice
                    print("Invalid choice. Please enter 1, 2, 3, or 4.")
        else:
            print("Incorrect PIN. Access denied.")
    else:
        print("Account not found. Please check the mobile number.")

# Main Menu
def main():
    while True:
        print("\n--- ATM System ---")
        print("1. Create Account")
        print("2. Access Account")
        print("3. Exit")
        choice = input("Enter your choice (1/2/3): ")

        if choice == "1":
            create_account()
        elif choice == "2":
            access_account()
        elif choice == "3":
            print("Thank you for using the ATM System. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

# Run the program
if __name__ == "__main__":
    main()

```
