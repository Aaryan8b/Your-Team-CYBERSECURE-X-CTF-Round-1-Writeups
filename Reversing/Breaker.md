# Breaker

"ok so in this chall i got a file that was AndroidBackup.ab so i madea py script to make the bkp into readable or iteratable form"
```python
import sys
from argparse import ArgumentParser

MAGIC = "$9$"

FAMILY = ["QzF3n6/9CAtpu0O", "B1IREhcSyrleKvMW8LXx", "7N-dVbwsY2g4oaJZGUDj", "iHkq.mPf5T"]
EXTRA = {}
for x, item in enumerate(FAMILY):
    for c in item:
        EXTRA[c] = 3 - x

NUM_ALPHA = list("".join(FAMILY))
ALPHA_NUM = {c: i for i, c in enumerate(NUM_ALPHA)}

ENCODING = [
    [1, 4, 32],
    [1, 16, 32],
    [1, 8, 32],
    [1, 64],
    [1, 32],
    [1, 4, 16, 128],
    [1, 32, 64]
]

def _nibble(cref, length):
    nib = cref[:length]
    rest = cref[length:]
    if len(nib) != length:
        print(f"[!] Ran out of characters: hit '{nib}', expecting {length} chars")
        sys.exit(1)
    return nib, rest

def _gap(c1, c2):
    return (ALPHA_NUM[c2] - ALPHA_NUM[c1]) % len(NUM_ALPHA) - 1

def _gap_decode(gaps, decode):
    if len(gaps) != len(decode):
        print("[!] Nibble and decode size not the same!")
        sys.exit(1)
    num = sum(gaps[i] * decode[i] for i in range(len(gaps)))
    return chr(num % 256)

def juniper_decrypt(crypt):
    if MAGIC not in crypt:
        print("[!] Not a $9$ encrypted string.")
        sys.exit(1)

    chars = crypt.split(MAGIC, 1)[1]
    first, chars = _nibble(chars, 1)
    toss, chars = _nibble(chars, EXTRA[first])
    prev = first
    decrypt = ""

    while chars:
        decode = ENCODING[len(decrypt) % len(ENCODING)]
        nibble, chars = _nibble(chars, len(decode))
        gaps = [_gap(prev, i) for i in nibble]
        prev = nibble[-1]
        decrypt += _gap_decode(gaps, decode)

    return decrypt

def main():
    parser = ArgumentParser(description="Juniper $9$ password decoder")
    parser.add_argument("encrypted", help="Encrypted $9$ string")

    args = parser.parse_args()

    print("[+] Junos $9$ password decoder")
    print(f"[+] Encrypted string: {args.encrypted}")
    print(f"[+] Decrypted string: {juniper_decrypt(args.encrypted)}")

if __name__ == "__main__":
    main()

```
"and which got me the tar file and on hunting in it i found an image at here backup\AndroidBackup\shared\0\Pictures"

![image](https://github.com/user-attachments/assets/5d095cce-d5b4-4359-b10a-e302ce0dc090)


### 🏁 Flag  
```
flag{tH1s_B@cKuP_n0t_pRot3cTed}
```
