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
  
## 

1. Write the script
    ``` python
    # prime_numbers.py
    # A spunky little script that hunts down prime numbers between 1 and 250
    # and drops them into results.txt like a boss.
    
    def is_prime(n):
        """Prime checker: because not all numbers are worthy."""
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
    
        # Print with some flair
        print("Boom! All done.")
        print(f"Counted {len(primes)} prime numbers between 1 and 250.")
        print(f"They're chilling in {file_path} — go take a look.")
    
    
    if __name__ == "__main__":
        main()
    ```  
   
3. Run the script
   ``` bash
   python3 steak_your_primes.py
   ```
4. Verify the output
   ``` bash
   cat results.txt
   ```


## Challenges
- ...

## Screenshot


## Takeaways
