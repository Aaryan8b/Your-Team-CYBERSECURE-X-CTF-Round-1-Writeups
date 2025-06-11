## Problem:

A mysterious executable has surfaced. No one knows what it does — yet. Can you uncover what's hidden beneath?

 [GhostPayload.exe](./resources/GhostPayload.exe)
 
 ---

## Solution:

- Extracted using 7zip

───GhostPayload
    └───.rsrc
        ├───MANIFEST
        └───SECRET

- SECRET had a file 103 written "ZmxhZ3tSRVZFUlNFX1RIRV9GTE9XXzB4OTB9"
- Its a base 64, flag{REVERSE_THE_FLOW_0x90}
