# Python Day6 Code

## Concept:Classes and Objects

### Python DayWise

```python
import random

class Account:
    def __init__(self, name, phone, balance, pin):
        self.name = name
        self.phone = phone
        self.balance = balance
        self.pin = pin

    # Function to check the account balance
    def check_balance(self):
        print(f"Your current balance is: ₹{self.balance}")

    # Function to deposit cash into the account
    def deposit_cash(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"₹{amount} deposited successfully!")
            self.check_balance()
        else:
            print("Invalid amount. Please enter a positive number.")

    # Function to withdraw cash from the account
    def withdraw_cash(self, amount):
        if amount <= 0:
            print("Invalid amount. Please enter a positive number.")
        elif amount > self.balance:
            print("Insufficient balance!")
        else:
            self.balance -= amount
            print(f"₹{amount} withdrawn successfully!")
            self.check_balance()

    # Function to reset the account PIN with OTP verification
    def reset_pin(self):
        phone_number = input("Enter your registered phone number: ")
        if phone_number == self.phone:
            otp = random.randint(1000, 9999)  # Generate a random 4-digit OTP
            print(f"OTP sent to your phone: {otp}")

            # Ask user to enter the OTP
            entered_otp = int(input("Enter the OTP sent to your phone: "))
            if entered_otp == otp:
                new_pin = input("Enter your new 4-digit PIN: ")
                self.pin = new_pin
                print("PIN has been reset successfully!")
            else:
                print("Invalid OTP. Please try again.")
        else:
            print("Phone number doesn't match our records. Please check your details.")

# Function for registering an account
def register():
    print("Registering your account...\n")
    name = input("Enter your full name: ")
    phone = input("Enter your phone number: ")
    pin = input("Enter a 4-digit PIN: ")
    balance = float(input("Enter your initial deposit amount: ₹"))

    account = Account(name, phone, balance, pin)
    print(f"Account registered successfully for {name}!")
    return account

# Main ATM menu allowing interaction with account functions
def main_menu(account):
    while True:
        print("\nATM Menu:")
        print("1. Check Balance")
        print("2. Deposit Cash")
        print("3. Withdraw Cash")
        print("4. Reset PIN")
        print("5. Exit")
        choice = input("Select an option (1-5): ")

        if choice == "1":
            account.check_balance()

        elif choice == "2":
            amount = float(input("Enter amount to deposit: ₹"))
            account.deposit_cash(amount)

        elif choice == "3":
            amount = float(input("Enter amount to withdraw: ₹"))
            account.withdraw_cash(amount)

        elif choice == "4":
            account.reset_pin()  # Reset PIN with OTP verification

        elif choice == "5":
            print("Exiting. Have a great day!")
            break

        else:
            print("Invalid choice. Please select a valid option.")

# Main entry point of the program
if __name__ == "__main__":
    print("Welcome to ATM Simulator!")

    # Registering the account and skipping login process
    account = register()
    main_menu(account)

```

### Python Main Code
```python
import random

class Account:
    def __init__(self, name, phone, balance, pin):
        self.name = name
        self.phone = phone
        self.balance = balance
        self.pin = pin

    # Function to check the account balance
    def check_balance(self):
        print(f"Your current balance is: ₹{self.balance}")

    # Function to deposit cash into the account
    def deposit_cash(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"₹{amount} deposited successfully!")
            self.check_balance()
        else:
            print("Invalid amount. Please enter a positive number.")

    # Function to withdraw cash from the account
    def withdraw_cash(self, amount):
        if amount <= 0:
            print("Invalid amount. Please enter a positive number.")
        elif amount > self.balance:
            print("Insufficient balance!")
        else:
            self.balance -= amount
            print(f"₹{amount} withdrawn successfully!")
            self.check_balance()

    # Function to reset the account PIN with OTP verification
    def reset_pin(self):
        phone_number = input("Enter your registered phone number: ")
        if phone_number == self.phone:
            otp = random.randint(1000, 9999)  # Generate a random 4-digit OTP
            print(f"OTP sent to your phone: {otp}")

            # Ask user to enter the OTP
            entered_otp = int(input("Enter the OTP sent to your phone: "))
            if entered_otp == otp:
                new_pin = input("Enter your new 4-digit PIN: ")
                self.pin = new_pin
                print("PIN has been reset successfully!")
            else:
                print("Invalid OTP. Please try again.")
        else:
            print("Phone number doesn't match our records. Please check your details.")

# Function for registering an account
def register():
    print("Registering your account...\n")
    name = input("Enter your full name: ")
    phone = input("Enter your phone number: ")
    pin = input("Enter a 4-digit PIN: ")
    balance = float(input("Enter your initial deposit amount: ₹"))

    account = Account(name, phone, balance, pin)
    print(f"Account registered successfully for {name}!")
    return account

# Main ATM menu allowing interaction with account functions
def main_menu(account):
    while True:
        print("\nATM Menu:")
        print("1. Check Balance")
        print("2. Deposit Cash")
        print("3. Withdraw Cash")
        print("4. Reset PIN")
        print("5. Exit")
        choice = input("Select an option (1-5): ")

        if choice == "1":
            account.check_balance()

        elif choice == "2":
            amount = float(input("Enter amount to deposit: ₹"))
            account.deposit_cash(amount)

        elif choice == "3":
            amount = float(input("Enter amount to withdraw: ₹"))
            account.withdraw_cash(amount)

        elif choice == "4":
            account.reset_pin()  # Reset PIN with OTP verification

        elif choice == "5":
            print("Exiting. Have a great day!")
            break

        else:
            print("Invalid choice. Please select a valid option.")

# Main entry point of the program
if __name__ == "__main__":
    print("Welcome to ATM Simulator!")

    # Registering the account and skipping login process
    account = register()
    main_menu(account)


```
