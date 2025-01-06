# Python Day2 Code

### Python DayWise

```python

print("--- Balance Operations ---")
current_balance = float(input("Enter your current balance: ₹"))  # Float to store balance
deposit_amount = float(input("Enter the amount to deposit: ₹"))  # Float for deposit amount


new_balance = current_balance + deposit_amount  # Adding deposit
print(f"Balance after deposit: ₹{new_balance}")


withdraw_amount = float(input("Enter the amount to withdraw: ₹"))  # Float for withdrawal amount
post_withdrawal_balance = new_balance - withdraw_amount  # Subtracting withdrawal
print(f"Balance after withdrawal: ₹{post_withdrawal_balance}")


```

### Python Main Code
```python

print("--- User Registration ---")
name = input("Enter your name: ")  # String
phone = input("Enter your mobile number: ")  # String

initial_balance = float(input("Enter your initial deposit amount: ₹"))  # Float

pin = input("Set your 4-digit PIN: ")  # String

print(f"\nRegistration Successful!")
print(f"Name: {name}, Phone: {phone}, Balance: ₹{initial_balance}, PIN: {pin}")

print("\n--- Balance Operations ---")
    
deposit_amount = float(input("Enter amount to deposit: ₹"))
new_balance = initial_balance + deposit_amount  # Adding deposit
print(f"Balance after deposit: ₹{new_balance}")

withdraw_amount = float(input("Enter amount to withdraw: ₹"))
    
post_withdrawal_balance = new_balance - withdraw_amount  # Subtraction
print(f"Balance after withdrawal: ₹{post_withdrawal_balance}")


```
