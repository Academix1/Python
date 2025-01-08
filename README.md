# Python Day7 Code

## Concept:File Handling

### Python DayWise

```python
# Day2 - File Handling: Saving account details in user_data.txt and OTP in otp_data.txt

# In Day2, Account class includes update_account_file to save changes to user_data.txt
def update_account_file(self):
    # Read the current account data from user_data.txt
    with open("user_data.txt", "r") as user_file:
        lines = user_file.readlines()

    # Find the line that matches the phone number (for the correct account)
    for i, line in enumerate(lines):
        user_data = line.strip().split(',')
        if user_data[1] == self.phone:
            # Update the line with the new balance and PIN
            lines[i] = f"{self.name},{self.phone},{self.balance},{self.pin}\n"
            break
    
    # Write the updated data back to user_data.txt
    with open("user_data.txt", "w") as user_file:
        user_file.writelines(lines)

# In Day2, OTP is stored in otp_data.txt with the creation time
def reset_pin(self):
    phone_number = input("Enter your registered phone number: ")
    if phone_number == self.phone:
        otp = random.randint(1000, 9999)  # Generate a random 4-digit OTP
        otp_creation_time = time.time()  # Record the time when OTP is generated

        # Save the OTP and time to otp_data.txt
        with open("otp_data.txt", "w") as otp_file:
            otp_file.write(f"{otp},{otp_creation_time}\n")

        print(f"OTP generated: {otp}. You have 5 minutes to enter it.")
        
        # Ask user to enter the OTP
        entered_otp = int(input("Enter the OTP sent to your phone: "))
        
        # Read the OTP and its creation time from otp_data.txt
        with open("otp_data.txt", "r") as otp_file:
            saved_otp, saved_time = otp_file.readline().strip().split(',')
            saved_otp = int(saved_otp)
            saved_time = float(saved_time)

        # Check if OTP is correct and within the time limit (5 minutes)
        if entered_otp == saved_otp:
            if time.time() - saved_time <= 300:  # 5 minutes = 300 seconds
                new_pin = input("Enter your new 4-digit PIN: ")
                self.pin = new_pin
                print("PIN has been reset successfully!")
                self.update_account_file()  # Update account details in the file
            else:
                print("OTP has expired. Please request a new OTP.")
        else:
            print("Invalid OTP. Please try again.")
    else:
        print("Phone number doesn't match our records. Please check your details.")

# Day2 - Login Function
def login():
    print("Login to your account...\n")
    pin = input("Enter your 4-digit PIN: ")

    # Read user data from user_data.txt
    with open("user_data.txt", "r") as user_file:
        user_data = user_file.readlines()
    
    for line in user_data:
        user_details = line.strip().split(',')
        stored_phone = user_details[1]
        stored_pin = user_details[3]
        
        if pin == stored_pin:
            # Login successful, return Account object
            print("Login successful!")
            account = Account(user_details[0], stored_phone, float(user_details[2]), stored_pin)
            return account
    print("Invalid phone number or PIN. Please try again.")
    return None

# Day2 - Main Menu Adjustments to allow login process and logout option
def main_menu(account):
    while True:
        print("\nATM Menu:")
        print("1. Check Balance")
        print("2. Deposit Cash")
        print("3. Withdraw Cash")
        print("4. Reset PIN")
        print("5. Logout")
        choice = input("Select an option (1-5): ")

        if choice == "1":
            account.check_balance()
            break  # After completing the action, exit to login screen

        elif choice == "2":
            amount = float(input("Enter amount to deposit: ₹"))
            account.deposit_cash(amount)
            break  # After completing the action, exit to login screen

        elif choice == "3":
            amount = float(input("Enter amount to withdraw: ₹"))
            account.withdraw_cash(amount)
            break  # After completing the action, exit to login screen

        elif choice == "4":
            account.reset_pin()  # Reset PIN with OTP verification
            break  # After completing the action, exit to login screen

        elif choice == "5":
            print("Logging out...")
            break  # Break the loop and go back to the main login/register screen

        else:
            print("Invalid choice. Please select a valid option.")

# Day2 - Login flow in the main entry point
if __name__ == "__main__":
    while True:
        print("\nWelcome to ATM Simulator!")
        print("1. Register")
        print("2. Login")
        print("3. Exit")
        option = input("Select an option (1-3): ")

        if option == "1":
            account = register()
            main_menu(account)
            continue  # After completing the actions, continue to the main login/register menu

        elif option == "2":
            account = login()
            if account:
                main_menu(account)
                continue  # After completing the actions, continue to the main login/register menu

        elif option == "3":
            print("Exiting. Have a great day!")
            break

        else:
            print("Invalid choice. Please select a valid option.")


```

### Python Main Code
```python
import random
import time

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
            self.update_account_file()  # Update account details in the file
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
            self.update_account_file()  # Update account details in the file

    # Function to reset the account PIN with OTP verification
    def reset_pin(self):
        phone_number = input("Enter your registered phone number: ")
        if phone_number == self.phone:
            otp = random.randint(1000, 9999)  # Generate a random 4-digit OTP
            otp_creation_time = time.time()  # Record the time when OTP is generated

            # Save the OTP and time to otp_data.txt
            with open("otp_data.txt", "w") as otp_file:
                otp_file.write(f"{otp},{otp_creation_time}\n")

            print(f"OTP generated: {otp}. You have 5 minutes to enter it.")

            # Ask user to enter the OTP
            entered_otp = int(input("Enter the OTP sent to your phone: "))
            
            # Read the OTP and its creation time from otp_data.txt
            with open("otp_data.txt", "r") as otp_file:
                saved_otp, saved_time = otp_file.readline().strip().split(',')
                saved_otp = int(saved_otp)
                saved_time = float(saved_time)

            # Check if OTP is correct and within the time limit (5 minutes)
            if entered_otp == saved_otp:
                if time.time() - saved_time <= 300:  # 5 minutes = 300 seconds
                    new_pin = input("Enter your new 4-digit PIN: ")
                    self.pin = new_pin
                    print("PIN has been reset successfully!")
                    self.update_account_file()  # Update account details in the file
                else:
                    print("OTP has expired. Please request a new OTP.")
            else:
                print("Invalid OTP. Please try again.")
        else:
            print("Phone number doesn't match our records. Please check your details.")

    # Function to update the account file with new details
    def update_account_file(self):
        # Read the current account data from user_data.txt
        with open("user_data.txt", "r") as user_file:
            lines = user_file.readlines()

        # Find the line that matches the phone number (for the correct account)
        for i, line in enumerate(lines):
            user_data = line.strip().split(',')
            if user_data[1] == self.phone:
                # Update the line with the new balance and PIN
                lines[i] = f"{self.name},{self.phone},{self.balance},{self.pin}\n"
                break
        
        # Write the updated data back to user_data.txt
        with open("user_data.txt", "w") as user_file:
            user_file.writelines(lines)

# Function for registering an account
def register():
    print("Registering your account...\n")
    name = input("Enter your full name: ")
    phone = input("Enter your phone number: ")
    pin = input("Enter a 4-digit PIN: ")
    balance = float(input("Enter your initial deposit amount: ₹"))

    # Save user data to user_data.txt
    with open("user_data.txt", "w") as user_file:
        user_file.write(f"{name},{phone},{balance},{pin}\n")
    
    account = Account(name, phone, balance, pin)
    print(f"Account registered successfully for {name}!")
    return account

# Function for logging into an existing account
def login():
    print("Login to your account...\n")
    pin = input("Enter your 4-digit PIN: ")

    # Read user data from user_data.txt
    with open("user_data.txt", "r") as user_file:
        user_data = user_file.readlines()
    
    for line in user_data:
        user_details = line.strip().split(',')
        stored_phone = user_details[1]
        stored_pin = user_details[3]
        
        if pin == stored_pin:
            # Login successful, return Account object
            print("Login successful!")
            account = Account(user_details[0], stored_phone, float(user_details[2]), stored_pin)
            return account
    print("Invalid phone number or PIN. Please try again.")
    return None

# Main ATM menu allowing interaction with account functions
# Main ATM menu allowing interaction with account functions
def main_menu(account):
    while True:
        print("\nATM Menu:")
        print("1. Check Balance")
        print("2. Deposit Cash")
        print("3. Withdraw Cash")
        print("4. Reset PIN")
        print("5. Logout")
        choice = input("Select an option (1-5): ")

        if choice == "1":
            account.check_balance()
            break  # After completing the action, exit to login screen

        elif choice == "2":
            amount = float(input("Enter amount to deposit: ₹"))
            account.deposit_cash(amount)
            break  # After completing the action, exit to login screen

        elif choice == "3":
            amount = float(input("Enter amount to withdraw: ₹"))
            account.withdraw_cash(amount)
            break  # After completing the action, exit to login screen

        elif choice == "4":
            account.reset_pin()  # Reset PIN with OTP verification
            break  # After completing the action, exit to login screen

        elif choice == "5":
            print("Logging out...")
            break  # Break the loop and go back to the main login/register screen

        else:
            print("Invalid choice. Please select a valid option.")


# Main entry point of the program
if __name__ == "__main__":
    while True:
        print("\nWelcome to ATM Simulator!")
        print("1. Register")
        print("2. Login")
        print("3. Exit")
        option = input("Select an option (1-3): ")

        if option == "1":
            account = register()
            main_menu(account)
            continue  # After completing the actions, continue to the main login/register menu

        elif option == "2":
            account = login()
            if account:
                main_menu(account)
                continue  # After completing the actions, continue to the main login/register menu

        elif option == "3":
            print("Exiting. Have a great day!")
            break

        else:
            print("Invalid choice. Please select a valid option.")



```
