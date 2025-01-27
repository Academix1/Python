# Python Day5 Code
## Collections
### Python DayWise

```python
name = input("Enter Name: ")
initial_balance = float(input("Enter Your Balance: "))
while initial_balance <= 0:
    print("Balance Should be greater than 0.")
    initial_balance = float(input("Enter Your Balance: "))

pin = input("Set Your PIN (4-digit): ")

while len(pin) != 4 or not pin.isdigit():
    print("Invalid PIN. Enter a 4-digit numeric PIN.")
    pin = input("Set Your PIN (4-digit): ")

def validate_pin(stored_pin, entered_pin):
    return stored_pin == entered_pin

def deposit(balance, damount):
    balance += damount
    return balance

def withdraw(balance, wamount):
    while wamount > balance:
        print("Withdrawal amount should not exceed the current balance.")
        wamount = float(input("Enter a valid Withdrawal Amount: "))
    balance -= wamount
    return balance

//[pause]
transaction_history = []

while True:
    re_rentered_pin = input("Enter Your PIN: ")
    if validate_pin(pin, re_rentered_pin):
        print(f"Welcome {name}!")
        while True:
            print("\nOptions:")
            print("1. Deposit")
            print("2. Withdraw")
            //[pause]
            print("3. View Transaction History")
            //[pause]
            print("4. Exit")
            choice = input("Enter your choice: ")

            if choice == "1":
                deposit_amount = float(input("Enter the amount to deposit: "))
                initial_balance = deposit(initial_balance, deposit_amount)
                transaction_history.append(
                    {"Type": "Deposit", "Amount": deposit_amount, "Balance": initial_balance}
                )
                print(f"Your current balance is: {initial_balance}")

            elif choice == "2":
                withdrawal_amount = float(input("Enter the amount to withdraw: "))
                initial_balance = withdraw(initial_balance, withdrawal_amount)
                transaction_history.append(
                    {"Type": "Withdraw", "Amount": withdrawal_amount, "Balance": initial_balance}
                )
                print(f"Your current balance is: {initial_balance}")
             //[pause]   
            elif choice == "3":
                //[pause]
                if not transaction_history:
                    print("No transactions available.")
                    //[pause]
                else:
                    print("\nTransaction History:")
                    //[pause]
                    for index, transaction in enumerate(transaction_history, start=1):
                    //[pause]
                        print(f"{index}. {transaction['Type']} - Amount: {transaction['Amount']} - Balance: {transaction['Balance']}")
                      //[pause]  

            elif choice == "4":
                print("Goodbye!")
                break
            else:
                print("Invalid choice. Please try again.")
    else:
        print("Incorrect PIN. Please try again.")


```
