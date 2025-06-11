# EnterpriseX

"ok so in this chall i ran the file and it seems to be generating code affording to my user name so it was "swadhin" in my case so i have to find the code to do that"

"here is the part i reversed via ghidra which makes the key"
![image](https://github.com/user-attachments/assets/ba1b55b9-c45f-44c5-ac0e-912c89d17dbe)

"so made a py code to find mine and entered it and got the flag"
```python
def generate_enterprise_key(username: str) -> str:
    uVar4 = 0

    for c in username:
        uVar4 = (uVar4 + ord(c)) & 0xFFFFFFFF
        shifted = (uVar4 >> 27) & 0xFFFFFFFF
        multiplied = (uVar4 * 0x20) & 0xFFFFFFFF
        uVar4 = (multiplied | shifted) ^ 0xA5A5A5A5
        uVar4 &= 0xFFFFFFFF  # Keep it 32-bit

    # Final transformation
    final = (((uVar4 ^ 0x1337BEEF) + 0xABCDEF) ^ 0x42) & 0xFFFFFFFF
    return f"X-{final:08X}"

# Example usage:
username = "swadhin"
print(generate_enterprise_key(username))

```
![image](https://github.com/user-attachments/assets/3e43bb88-ddb1-4950-a8bd-014cf45ad7bc)


### 🏁 Flag  
```
flag{l1c3ns3d_t0_h4ck}
```
