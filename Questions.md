### Concept: File Handling

---

### 1. **How would you update the account data in a file for a given user?**
   * **Answer:**
     ```python
     def update_account_file(self):
         with open("user_data.txt", "r") as user_file:
             lines = user_file.readlines()

         for i, line in enumerate(lines):
             user_data = line.strip().split(',')
             if user_data[1] == self.phone:
                 lines[i] = f"{self.name},{self.phone},{self.balance},{self.pin}\n"
                 break
         
         with open("user_data.txt", "w") as user_file:
             user_file.writelines(lines)
     ```

---

### 2. **How would you store an OTP with its creation time in a file?**
   * **Answer:**
     ```python
     import random
     import time

     def generate_and_store_otp(self):
         otp = random.randint(1000, 9999)
         otp_creation_time = time.time()

         with open("otp_data.txt", "w") as otp_file:
             otp_file.write(f"{otp},{otp_creation_time}\n")

         print(f"OTP generated: {otp}. You have 5 minutes to enter it.")
     ```

---

### 3. **How would you verify an OTP and check if it is expired?**
   * **Answer:**
     ```python
     def verify_otp(self, entered_otp):
         with open("otp_data.txt", "r") as otp_file:
             saved_otp, saved_time = otp_file.readline().strip().split(',')
             saved_otp = int(saved_otp)
             saved_time = float(saved_time)

         if entered_otp == saved_otp:
             if time.time() - saved_time <= 300:  # OTP expiry check (5 minutes)
                 print("OTP verified successfully!")
             else:
                 print("OTP has expired. Please request a new OTP.")
         else:
             print("Invalid OTP. Please try again.")
     ```

---

### 4. **How would you implement a login functionality that verifies the user's PIN from a file?**
   * **Answer:**
     ```python
     def login():
         print("Login to your account...")
         pin = input("Enter your 4-digit PIN: ")

         with open("user_data.txt", "r") as user_file:
             user_data = user_file.readlines()
         
         for line in user_data:
             user_details = line.strip().split(',')
             stored_phone = user_details[1]
             stored_pin = user_details[3]
             
             if pin == stored_pin:
                 print("Login successful!")
                 account = Account(user_details[0], stored_phone, float(user_details[2]), stored_pin)
                 return account
         print("Invalid phone number or PIN. Please try again.")
         return None
     ```

---

### 5. **How would you handle file write mode when registering a new user?**
   * **Answer:**
     ```python
     def register():
         name = input("Enter your name: ")
         phone = input("Enter your phone number: ")
         balance = float(input("Enter initial balance: ₹"))
         pin = input("Enter your 4-digit PIN: ")

         with open("user_data.txt", "a") as user_file:
             user_file.write(f"{name},{phone},{balance},{pin}\n")

         print("Account registered successfully!")
     ```

---

### 6. **How would you handle errors while reading user data from a file?**
   * **Answer:**
     ```python
     def read_account_data():
         try:
             with open("user_data.txt", "r") as user_file:
                 user_data = user_file.readlines()
             return user_data
         except FileNotFoundError:
             print("Error: user_data.txt file not found.")
             return []
     ```

---

### 7. **How would you manage multiple OTP entries for different users?**
   * **Answer:**
     ```python
     def generate_and_store_multiple_otps(self):
         otp = random.randint(1000, 9999)
         otp_creation_time = time.time()

         with open("otp_data.txt", "a") as otp_file:
             otp_file.write(f"{otp},{otp_creation_time}\n")

         print(f"OTP generated: {otp}. You have 5 minutes to enter it.")
     ```

---

### 8. **How would you improve file integrity while updating the account information?**
   * **Answer:**
     ```python
     import os
     import tempfile

     def update_account_file(self):
         temp_file = tempfile.NamedTemporaryFile(delete=False)
         
         with open("user_data.txt", "r") as user_file:
             lines = user_file.readlines()

         with open(temp_file.name, "w") as temp:
             for line in lines:
                 user_data = line.strip().split(',')
                 if user_data[1] == self.phone:
                     line = f"{self.name},{self.phone},{self.balance},{self.pin}\n"
                 temp.write(line)

         os.replace(temp_file.name, "user_data.txt")
     ```

---

### 9. **How would you securely store and retrieve sensitive data like a user's PIN?**
   * **Answer:**
     ```python
     from cryptography.fernet import Fernet

     def generate_key():
         return Fernet.generate_key()

     def encrypt_data(data, key):
         f = Fernet(key)
         return f.encrypt(data.encode())

     def decrypt_data(encrypted_data, key):
         f = Fernet(key)
         return f.decrypt(encrypted_data).decode()

     # Example usage for storing and checking PIN:
     key = generate_key()
     encrypted_pin = encrypt_data(self.pin, key)

     # Save encrypted PIN
     with open("user_data.txt", "a") as user_file:
         user_file.write(f"{self.name},{self.phone},{self.balance},{encrypted_pin}\n")

     # When verifying PIN during login
     with open("user_data.txt", "r") as user_file:
         user_data = user_file.readlines()

     for line in user_data:
         user_details = line.strip().split(',')
         stored_encrypted_pin = user_details[3]
         stored_pin = decrypt_data(stored_encrypted_pin.encode(), key)
         if stored_pin == self.pin:
             print("Login successful!")
             break
     ```

---

### 10. **How would you lock a file to prevent race conditions during updates?**
   * **Answer:**
     ```python
     import fcntl

     def update_account_file(self):
         with open("user_data.txt", "r+") as user_file:
             # Lock the file to prevent other processes from accessing it
             fcntl.flock(user_file, fcntl.LOCK_EX)

             lines = user_file.readlines()

             for i, line in enumerate(lines):
                 user_data = line.strip().split(',')
                 if user_data[1] == self.phone:
                     lines[i] = f"{self.name},{self.phone},{self.balance},{self.pin}\n"
                     break
             
             user_file.seek(0)
             user_file.writelines(lines)

             # Unlock the file after writing
             fcntl.flock(user_file, fcntl.LOCK_UN)
     ```

---

Let me know if you need further clarifications or modifications!
