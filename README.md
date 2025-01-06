# Python Day3 Code

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

# Balance Operations
print("\n--- Balance Operations ---")

while True:  # Loop for performing multiple operations
    print("\nAvailable Operations:")
    print("1. Deposit Amount")
    print("2. Withdraw Amount")
    print("3. Exit")
    choice = input("Enter your choice (1/2/3): ")

    if choice == "1":  # Deposit Operation
        deposit_amount = float(input("Enter amount to deposit: ₹"))
        while deposit_amount <= 0:  # Loop for valid deposit amount
            print("Deposit amount must be greater than ₹0.")
            deposit_amount = float(input("Enter amount to deposit: ₹"))
        initial_balance += deposit_amount
        print(f"Balance after deposit: ₹{initial_balance}")

    elif choice == "2":  # Withdrawal Operation
        withdraw_amount = float(input("Enter amount to withdraw: ₹"))
        while withdraw_amount <= 0:  # Loop for valid withdrawal amount
            print("Withdrawal amount must be greater than ₹0.")
            withdraw_amount = float(input("Enter amount to withdraw: ₹"))
        if withdraw_amount > initial_balance:  # Conditional check for balance
            print("Insufficient balance!")
        else:
            initial_balance -= withdraw_amount
            print(f"Balance after withdrawal: ₹{initial_balance}")

    elif choice == "3":  # Exit
        print("Thank you for using our services. Goodbye!")
        break

    else:  # Invalid Choice
        print("Invalid choice. Please enter 1, 2, or 3.")


```
