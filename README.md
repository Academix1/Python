# Python Day3 Code

## Concept:Loops and Conditional Statements 

### Python DayWise

```python

# Loop for PIN validation
pin = input("Set your 4-digit PIN: ")
while True:
    entered_pin = input("Enter your 4-digit PIN to validate: ")
    if entered_pin == pin:
        print("PIN Verified!")
        break  # Exit loop if PIN is correct
    else:
        print("Incorrect PIN. Try again.")

# Menu with conditional logic
print("\nATM Menu:")
print("1. Check Balance")
print("2. Deposit Cash")
print("3. Withdraw Cash")
print("4. Exit")
choice = input("Choose an option (1-4): ")

if choice == "1":
    print("Check Balance selected.")
elif choice == "2":
    print("Deposit Cash selected.")
elif choice == "3":
    print("Withdraw Cash selected.")
elif choice == "4":
    print("Exit selected.")
else:
    print("Invalid choice. Please try again.")



```

### Python Main Code
```python

name=str(input("Enter Name"))

inital_balance=float(input("Enter Your balance"))
while inital_balance<=0:
    print("Balance Should be > than 0")
    inital_balance=float(input("Enter Your Balance "))

pin=input("Enter Your Pin")
while len(pin)!=4 or not pin.isdigit():
    print("Invalid Pin Enter 4 Digit PIN(Number)")
    pin=input("Enter the PIN")

while True:
    print("1.Deposit")
    print("2.Witdrawl")
    print("3.Exit")
    choice=int(input("Enter Your Choice 1/2/3"))

    if choice==1:
        deposit=float(input("Enter Your Deposit Amount :"))
        inital_balance+=deposit
    elif choice==2:
        withdrawl=float(input("Enter Your Number: "))
        while withdrawl>inital_balance:
            print("Withdrtawl Should be lessthan Inital Balance")
            withdrawl=float(input("Enter Your Withdrawl: "))
        if inital_balance>withdrawl:
            inital_balance-=withdrawl
            print("Initial balance after Withdrawl ",inital_balance)
        else:
            print("Insufficient Funds")
    elif choice>=3:
        print("Thanks For Visiting !")
        break

```
