Here are the answers to the questions:

1. **How would you calculate the new balance by adding the deposit amount to the current balance?**  
   ```python
   new_balance = current_balance + deposit_amount
   ```

2. **How would you find the balance after withdrawal by subtracting the withdrawal amount from the new balance?**  
   ```python
   post_withdrawal_balance = new_balance - withdraw_amount
   ```

3. **How would you collect the user's current balance and store it as a float?**  
   ```python
   current_balance = float(input("Enter your current balance: ₹"))
   ```

4. **How would you ask for the deposit amount and convert it into a float?**  
   ```python
   deposit_amount = float(input("Enter the amount to deposit: ₹"))
   ```

5. **How would you get the withdrawal amount from the user and convert it into a float?**  
   ```python
   withdraw_amount = float(input("Enter the amount to withdraw: ₹"))
   ```

6. **How would you display the updated balance after the deposit is made, including the currency symbol?**  
   ```python
   print(f"Balance after deposit: ₹{new_balance}")
   ```

7. **How would you display the remaining balance after the withdrawal, including the currency symbol?**  
   ```python
   print(f"Balance after withdrawal: ₹{post_withdrawal_balance}")
   ```
