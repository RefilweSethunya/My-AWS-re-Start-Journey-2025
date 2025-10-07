# Python Lab: Python Exercise

## Objective
- Write a Python script to display all prime numbers between 1 and 250.
- Store the output in a file named results.txt.
- Run and test the script to verify that the expected results are produced.
- Save the script and record its absolute path for future reference.
- Use Python 3 to execute the script with the command (replacing file.py with your file name):
  ``` bash
  python3 file.py
  ```
  
## Steps Taken
1. Write the script for prime_and_proper.py using nano editor
   ``` bash
   nano prime_and_proper.py
   ```

    Copy and Paste the following lines into nano
   ``` python
    # prime_and_proper.py is the name of the file 
    # My spunky little script that hunts down prime numbers between 1 and 250
    # afterwards output them into results.txt
    
    def is_prime(n):
        if n < 2:
            return False
        for i in range(2, int(n**0.5) + 1):
            if n % i == 0:
                return False
        return True
    
    
    def main():
        # Generate prime numbers between 1 and 250
        primes = [str(num) for num in range(1, 251) if is_prime(num)]
    
        # Save primes to results.txt
        file_path = "results.txt"
        with open(file_path, "w") as f:
            f.write("\n".join(primes))
    
        # Prints to user
        print("Ta-da! All done.")
        print(f"Counted {len(primes)} prime numbers between 1 and 250.")
        print(f"They're chilling in {file_path} — go take a look.")
    
    
    if __name__ == "__main__":
        main()
    ```  
   Save and exit nano
3. Run the script
   ``` bash
   python3 prime_and_proper.py
   ```
4. Verify the output
   ``` bash
   cat results.txt
   ```


## Challenges
- ...

## Screenshot
CLI
<img width="1366" height="725" alt="image" src="https://github.com/user-attachments/assets/e2bd95cd-5a2f-4449-a3a0-0b51995c9ffa" />
The script in nano editor
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/bcfc5d6b-58ff-4021-a525-657265a7e7e8" />
Displaying the results from results.txt
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/14b4e09c-9eaa-41bc-85f2-3baa3e89b7c1" />


## Takeaways
Using nano editor, I had forgotten that to save and exit we press CTRL + O (that’s the letter O, not zero) and then press Enter to confirm.<br>
To exit without saving, we press CTRL + X .
