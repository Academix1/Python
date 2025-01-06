# Python Day1 Code

### Python DayWise

```python
# Collecting user data for demonstration
name = input("Enter your name: ")  # String
phone = input("Enter your mobile number: ")  # String for storing phone numbers
try:
    initial_balance = float(input("Enter your initial deposit amount: ₹"))  # Float
except ValueError:
    initial_balance = 0.0
    print("Invalid input for balance. Setting it to ₹0.")
pin = input("Set your 4-digit PIN: ")  # String

print(f"Name: {name}, Phone: {phone}, Balance: ₹{initial_balance}, PIN: {pin}")
```

### Python Main Code
```python
# Collecting user data for demonstration
name = input("Enter your name: ")  # String
phone = input("Enter your mobile number: ")  # String for storing phone numbers
try:
    initial_balance = float(input("Enter your initial deposit amount: ₹"))  # Float
except ValueError:
    initial_balance = 0.0
    print("Invalid input for balance. Setting it to ₹0.")
pin = input("Set your 4-digit PIN: ")  # String

print(f"Name: {name}, Phone: {phone}, Balance: ₹{initial_balance}, PIN: {pin}")
```
