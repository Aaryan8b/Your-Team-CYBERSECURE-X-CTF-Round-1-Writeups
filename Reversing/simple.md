# simple

"ok so in this chall we have a gat file whihc askin for 'gate's access code so maade a py code to brute the code hoping for the best"
```python
import subprocess
import itertools
import string

def test_access_code(code):
    # Run ./gate and submit the code
    process = subprocess.Popen(
        ["./gate"],
        stdin=subprocess.PIPE,
        stdout=subprocess.PIPE,
        stderr=subprocess.PIPE,
        text=True
    )
    # Send the code + newline (simulate Enter)
    stdout, stderr = process.communicate(input=code + "\n")
    return stdout

def brute_force_with_io():
    charset = string.ascii_letters + string.digits + string.punctuation
    max_attempts = 100000  # Prevent infinite loops
    attempts = 0

    for candidate in itertools.product(charset, repeat=6):
        code = ''.join(candidate)
        attempts += 1
        if attempts > max_attempts:
            print("Reached max attempts. Stopping.")
            break

        output = test_access_code(code)
        print(f"Trying: {code} => Output: {output.strip()}")

        if "Access Denied" not in output:
            print(f"SUCCESS! Valid code: {code}")
            break

if __name__ == "__main__":
    brute_force_with_io()
```
"and found hte code which was 'aaaa+;' "
![image](https://github.com/user-attachments/assets/e1e213e3-7652-4bde-880f-370f98103bdb)
"then decipher it with xor and found at 12"
![image](https://github.com/user-attachments/assets/8f5943df-fd38-4202-aa65-050f5cc0ab9c)

### 🏁 Flag  
```
flag{n1mr0d_w0rks}
```
