# Python Day6 Code

## Concept:Classes and Objects(OOPS)

### Python DayWise

```python
class ATM:
    def __init__(self, name, initial_balance, pin):
        self.name = name
        self.balance = initial_balance
        self.pin = pin
        self.transaction_history = []

    def validate_pin(self, entered_pin):
        return self.pin == entered_pin

    def deposit(self, amount):
        self.balance += amount
        self.transaction_history.append(
            {"Type": "Deposit", "Amount": amount, "Balance": self.balance}
        )
        return self.balance

    def withdraw(self, amount):
        while amount > self.balance:
            print("Withdrawal amount should not exceed the current balance.")
            amount = float(input("Enter a valid Withdrawal Amount: "))
        self.balance -= amount
        self.transaction_history.append(
            {"Type": "Withdraw", "Amount": amount, "Balance": self.balance}
        )
        return self.balance

    def view_transaction_history(self):
        if not self.transaction_history:
            print("No transactions available.")
        else:
            print("\nTransaction History:")
            for index, transaction in enumerate(self.transaction_history, start=1):
                print(
                    f"{index}. {transaction['Type']} - Amount: {transaction['Amount']} - Balance: {transaction['Balance']}"
                )

name = input("Enter Name: ")

initial_balance = float(input("Enter Your Balance: "))
while initial_balance <= 0:
    print("Balance Should be greater than 0.")
    initial_balance = float(input("Enter Your Balance: "))

pin = input("Set Your PIN (4-digit): ")
while len(pin) != 4 or not pin.isdigit():
    print("Invalid PIN. Enter a 4-digit numeric PIN.")
    pin = input("Set Your PIN (4-digit): ")


atm = ATM(name, initial_balance, pin)

while True:
    entered_pin = input("Enter Your PIN: ")
    if atm.validate_pin(entered_pin):
        print(f"Welcome {atm.name}!")
        while True:
            print("\nOptions:")
            print("1. Deposit")
            print("2. Withdraw")
            print("3. View Transaction History")
            print("4. Exit")
            choice = input("Enter your choice: ")

            if choice == "1":
                deposit_amount = float(input("Enter the amount to deposit: "))
                atm.deposit(deposit_amount)
                print(f"Your current balance is: {atm.balance}")

            elif choice == "2":
                withdrawal_amount = float(input("Enter the amount to withdraw: "))
                atm.withdraw(withdrawal_amount)
                print(f"Your current balance is: {atm.balance}")

            elif choice == "3":
                atm.view_transaction_history()

            elif choice == "4":
                print("Goodbye!")
                break
            else:
                print("Invalid choice. Please try again.")
    else:
        print("Incorrect PIN. Please try again.")

```
