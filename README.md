# Blockchain Technology Lab (CS493) — Practical Exam & Viva Guide

> **Course:** Blockchain Technology Lab (CS493) — Final Year B.Tech. (CSE)  
> **References:** `CAS BT lab with Rurics by GSW.pdf`, `simple_blockchain (1).ipynb` (Exp. 4), `Exp.7_SimpleToken_Remix.pdf` (Exp. 7)  
> **Purpose:** Complete step-by-step implementation guide + expected outputs + oral/viva questions for all **8 practicals**.

---

## Pre-Exam Checklist (Do This Before Tomorrow's Practical!)

- [ ] **Python 3** installed (`python3 --version`).
- [ ] **Install `cryptography` library** for Practical 5:
  ```bash
  pip install cryptography
  ```
  *(A zero-dependency pure-Python backup is also included in Practical 5 in case `pip` or internet is unavailable on the lab PC.)*
- [ ] **MetaMask browser extension** installed in Chrome/Brave with a wallet created.
- [ ] **Sepolia Testnet enabled** in MetaMask (`Settings → Advanced → Show test networks` or Network dropdown → `Show test networks` → select **Sepolia**).
- [ ] **Get free SepoliaETH tonight** (faucets have daily limits/queues) using:
  - Google Cloud Web3 Faucet: https://cloud.google.com/application/web3/faucet/ethereum/sepolia
  - Alchemy Sepolia Faucet: https://www.alchemy.com/faucets/ethereum-sepolia
  - Chainlink Faucet: https://faucets.chain.link/sepolia
- [ ] **Bookmark Remix IDE:** https://remix.ethereum.org/
- [ ] **Bookmark Sepolia Etherscan:** https://sepolia.etherscan.io/

> **Rubric Tip (30 Marks per Practical):**  
> Problem Understanding (5) + Coding Performance (15) + Documentation/Comments (5) + Timely Submission (5).  
> Always keep your code **well-commented**, explain **what each function does**, and **demonstrate edge cases** (e.g., tampering a block or sending more tokens than balance).

---

## Table of Contents

1. [Practical 1: Fundamental Concepts, History, Evolution & Characteristics of Blockchain](#practical-1-fundamental-concepts-history-evolution--characteristics-of-blockchain)
2. [Practical 2: Blockchain Data Structures (Blocks, Chains, Merkle Trees) & Consensus (PoW, PoS)](#practical-2-blockchain-data-structures--consensus-mechanisms)
3. [Practical 3: Implement SHA-256 Hashing in Python & Observe Avalanche Effect](#practical-3-implement-sha-256-hashing-in-python)
4. [Practical 4: Build a Simple Blockchain in Python & Verify Chain Integrity](#practical-4-build-a-simple-blockchain-in-python)
5. [Practical 5: Public/Private Key Generation, Message Signing & Verification in Python](#practical-5-key-pair-generation-message-signing--verification-in-python)
6. [Practical 6: Write & Deploy "Hello World" Smart Contract on Remix IDE (Solidity)](#practical-6-hello-world-smart-contract-on-remix-ide)
7. [Practical 7: Simple Token Transfer Smart Contract on Remix VM](#practical-7-simple-token-transfer-smart-contract-on-remix-vm)
8. [Practical 8: Deploy Smart Contract on Ethereum Sepolia Testnet via MetaMask & Verify on Etherscan](#practical-8-deploy-on-ethereum-sepolia-testnet--verify-on-etherscan)
9. [Rapid-Fire General Viva Questions (Cheat Sheet)](#rapid-fire-general-viva-questions-cheat-sheet)

---

## Practical 1: Fundamental Concepts, History, Evolution & Characteristics of Blockchain

### Aim
To study and understand the fundamental concepts of blockchain technology, its history, evolution, and key characteristics (decentralization, transparency, immutability).

### Simple Steps to Perform / Present
Since this is a **study-based practical**, prepare to explain these 4 pillars cleanly (on paper, slides, or verbally during viva):

1. **Define Blockchain:**
   - A **distributed, decentralized, append-only digital ledger** that stores transactions in chronologically linked **blocks** secured by **cryptography**.
   - Every participating node keeps a copy of the ledger; no central authority (like a bank) is needed.
2. **Trace the History & Evolution:**
   - **1991:** Stuart Haber & W. Scott Stornetta introduced cryptographically timestamped chains of documents.
   - **1992:** Merkle trees were incorporated to bundle multiple documents into one block.
   - **2008:** Satoshi Nakamoto published the Bitcoin whitepaper (*"Bitcoin: A Peer-to-Peer Electronic Cash System"*).
   - **2009 (Blockchain 1.0 — Currency):** Bitcoin Genesis Block mined; peer-to-peer digital money.
   - **2015 (Blockchain 2.0 — Smart Contracts):** Vitalik Buterin launched **Ethereum**, introducing programmable smart contracts and DApps.
   - **2018+ (Blockchain 3.0 — Scalability & Interoperability):** High-throughput chains, DeFi, NFTs, Layer-2 rollups, enterprise chains (Hyperledger Fabric, Solana, Polygon, Polkadot).
3. **Explain the Key Characteristics:**
   - **Decentralization:** No single point of failure or central control; consensus is shared across peer nodes.
   - **Transparency:** On public blockchains, every transaction is visible to all participants (pseudonymous addresses, public balances/history).
   - **Immutability:** Once data is recorded and confirmed in a block, altering it requires changing the hash of that block and *every* subsequent block across >50% of the network — practically impossible.
   - **Security & Trustlessness:** Secured via cryptographic hashing and digital signatures; parties transact without needing to trust each other.
4. **Compare Types of Blockchain:**
   | Type | Access | Examples | Use Case |
   | :--- | :--- | :--- | :--- |
   | **Public (Permissionless)** | Anyone can join & validate | Bitcoin, Ethereum | Cryptocurrencies, DeFi |
   | **Private (Permissioned)** | Single organization controls access | Hyperledger Fabric, R3 Corda | Internal enterprise audit |
   | **Consortium (Federated)** | Group of organizations governs | Quorum, Energy Web Chain | Banking & supply chain networks |

### Important Oral / Viva Questions (Practical 1)
1. **What is Blockchain in one sentence?**  
   A decentralized, distributed, immutable ledger that records transactions in cryptographically linked blocks across a peer-to-peer network.
2. **How is Blockchain different from a traditional centralized database?**  
   Traditional databases are controlled by a single admin and support CRUD (Create, Read, Update, Delete). Blockchains are distributed, append-only (Create & Read), and require network consensus to add data.
3. **What is the double-spending problem, and how does Blockchain solve it?**  
   Double-spending is spending the same digital currency twice. Blockchain solves it using a shared chronological ledger, cryptographic verification, and a consensus mechanism (like PoW/PoS) so only one valid transaction is accepted.
4. **What is the difference between Decentralization and Distribution?**  
   *Distributed* means data/computation is spread across multiple machines. *Decentralized* means no single entity has control over those machines. A system can be distributed yet centralized (e.g., Google servers), whereas public blockchains are both.
5. **Is Blockchain anonymous or pseudonymous?**  
   Pseudonymous. Users are identified by public wallet addresses (hex strings) rather than real names, but all transactions linked to an address are publicly traceable.
6. **What is Blockchain 1.0 vs 2.0 vs 3.0?**  
   1.0 = Cryptocurrencies (Bitcoin); 2.0 = Smart Contracts & DApps (Ethereum); 3.0 = Scalable, interoperable, enterprise & Web3 applications.

---

## Practical 2: Blockchain Data Structures & Consensus Mechanisms

### Aim
To study blockchain data structures (blocks, chains, Merkle trees) and consensus mechanisms (Proof of Work, Proof of Stake).

### Simple Steps to Perform / Present
Be ready to draw and explain the following **3 diagrams/concepts**:

1. **Structure of a Block & Chain:**
   Each block has a **Block Header** and **Block Body (Transactions)**:
   ```text
   +-----------------------------------+       +-----------------------------------+
   |            BLOCK #1               |       |            BLOCK #2               |
   +-----------------------------------+       +-----------------------------------+
   | Index / Height: 1                 |       | Index / Height: 2                 |
   | Timestamp:      1710000000        |       | Timestamp:      1710000600        |
   | Prev Hash:      0000abc... (B0)   |  <--- | Prev Hash:      0000def... (B1)   |
   | Merkle Root:    9f8e7d...         |       | Merkle Root:    4a3b2c...         |
   | Nonce:          48291             |       | Nonce:          91042             |
   | Current Hash:   0000def...        |       | Current Hash:   0000777...        |
   +-----------------------------------+       +-----------------------------------+
   | Transactions: [Tx1, Tx2, ...]     |       | Transactions: [Tx3, Tx4, ...]     |
   +-----------------------------------+       +-----------------------------------+
   ```
   - **Genesis Block:** The very first block (Block `0`) whose `Previous Hash` is `000...0`.
   - **Hash Pointer:** Each block stores the hash of the previous block, creating a tamper-evident chain.

2. **Merkle Tree (Hash Tree):**
   ```text
                 [ Merkle Root = Hash(H12 + H34) ]
                       /                   \
          [ H12 = Hash(H1 + H2) ]     [ H34 = Hash(H3 + H4) ]
               /          \                /          \
        [ H1=H(Tx1) ] [ H2=H(Tx2) ] [ H3=H(Tx3) ] [ H4=H(Tx4) ]
              |             |             |             |
             Tx1           Tx2           Tx3           Tx4
   ```
   - Leaf nodes = hashes of individual transactions.
   - Non-leaf nodes = hash of the concatenation of their two child hashes.
   - **Purpose:** Efficiently verify whether a transaction belongs to a block in $O(\log n)$ time without downloading all transactions (used in SPV / light wallets).

3. **Consensus Mechanisms — Proof of Work (PoW) vs Proof of Stake (PoS):**
   | Feature | Proof of Work (PoW) | Proof of Stake (PoS) |
   | :--- | :--- | :--- |
   | **Participants** | Miners | Validators |
   | **How block is chosen** | First to find a `nonce` such that `Hash(block) < target` (leading zeros) | Randomly selected proportional to staked cryptocurrency |
   | **Security / Penalty** | High electricity & hardware cost | **Slashing** (validators lose staked coins for cheating) |
   | **Energy Usage** | Very high | Very low (~99.95% less than PoW) |
   | **Speed / Throughput** | Slower | Faster finality |
   | **Examples** | Bitcoin, Litecoin | Ethereum (post-Merge), Cardano, Solana |

### Important Oral / Viva Questions (Practical 2)
1. **What is a Genesis Block?**  
   The first block of a blockchain (index 0). It has no parent block, so its previous hash is set to `"0"`.
2. **What is a Nonce?**  
   "Number used once" — a counter value that miners repeatedly change in PoW until the block's hash meets the network's difficulty target (e.g., starts with `0000`).
3. **Why do blockchains use a Merkle Tree instead of just hashing all transactions together?**  
   A Merkle tree allows **fast membership verification** (Merkle Proof) in $O(\log n)$ hashes. A light client only needs the Merkle Root and sibling hashes along the path to verify a transaction.
4. **What happens if there is an odd number of transactions in a Merkle Tree?**  
   The last transaction's hash is duplicated to make an even pair so it can be hashed together.
5. **What is a 51% Attack?**  
   When an attacker controls more than 50% of the network's mining power (PoW) or staked coins (PoS), allowing them to halt transactions or perform double-spending.
6. **What is Slashing in Proof of Stake?**  
   A penalty mechanism where a validator's staked crypto is partially or fully destroyed if they act maliciously (e.g., signing two conflicting blocks) or go offline repeatedly.

---

## Practical 3: Implement SHA-256 Hashing in Python

### Aim
To implement SHA-256 hashing in Python and observe how changes in data affect the hash output.

### Simple Step-by-Step Implementation

**Step 1:** Create a file named `exp3_sha256.py`.  
**Step 2:** Write the following code:

```python
import hashlib

def compute_sha256(data: str) -> str:
    """Computes and returns the 64-character hexadecimal SHA-256 hash of a string."""
    encoded_data = data.encode("utf-8")         # Convert string to bytes
    hash_object = hashlib.sha256(encoded_data)  # Apply SHA-256 algorithm
    return hash_object.hexdigest()              # Return 64-char hex string

def bit_difference(hash1: str, hash2: str) -> tuple[int, float]:
    """Counts how many bits differ between two hex hashes (Avalanche Effect)."""
    bin1 = bin(int(hash1, 16))[2:].zfill(256)
    bin2 = bin(int(hash2, 16))[2:].zfill(256)
    diff_bits = sum(b1 != b2 for b1, b2 in zip(bin1, bin2))
    percentage = (diff_bits / 256) * 100
    return diff_bits, percentage

if __name__ == "__main__":
    # 1. Original Input
    text1 = "Hello Blockchain"
    # 2. Minor change: single character changed ('H' -> 'h')
    text2 = "hello Blockchain"
    # 3. Minor change: extra space/punctuation added
    text3 = "Hello Blockchain."

    h1 = compute_sha256(text1)
    h2 = compute_sha256(text2)
    h3 = compute_sha256(text3)

    print(f"Input 1 : '{text1}'\nSHA-256 : {h1} (length = {len(h1)} hex chars)\n")
    print(f"Input 2 : '{text2}'\nSHA-256 : {h2}\n")
    print(f"Input 3 : '{text3}'\nSHA-256 : {h3}\n")

    # Demonstrate Avalanche Effect
    diff, pct = bit_difference(h1, h2)
    print(f"Avalanche Effect (Input 1 vs Input 2): {diff}/256 bits changed ({pct:.2f}%)")

    # Demonstrate Determinism (same input always gives same hash)
    print("Deterministic check (same input again matches?):", compute_sha256(text1) == h1)
```

**Step 3:** Run the program in terminal:
```bash
python3 exp3_sha256.py
```

### What to Demonstrate to the Examiner
- **Fixed Length:** Whether the input is 1 character or a whole paragraph, output is always **256 bits = 64 hexadecimal characters**.
- **Avalanche Effect:** Changing just `'H'` to `'h'` changes ~50% of the output bits completely.
- **Deterministic:** Running SHA-256 on `"Hello Blockchain"` again yields the exact same hash.

### Important Oral / Viva Questions (Practical 3)
1. **What does SHA-256 stand for?**  
   Secure Hash Algorithm 256-bit (part of the SHA-2 family designed by NSA/NIST).
2. **What is the output size of SHA-256 in bits, bytes, and hex characters?**  
   256 bits = 32 bytes = 64 hexadecimal characters (since 1 hex character = 4 bits).
3. **What is the Avalanche Effect?**  
   A tiny change in input (even 1 bit or 1 letter) produces a drastically different hash (~50% of bits flip), making it impossible to predict output changes.
4. **Can you decrypt a SHA-256 hash back to the original message?**  
   No. Hashing is a **one-way function** (pre-image resistant). Unlike encryption, there is no key to reverse it.
5. **What are the 5 key properties of a cryptographic hash function?**  
   1) Deterministic, 2) Fixed output size, 3) Pre-image resistant (one-way), 4) Avalanche effect, 5) Collision resistant (hard to find two different inputs with the same hash).
6. **Why did we use `.encode("utf-8")` in Python?**  
   `hashlib.sha256()` operates on raw **bytes**, not Python strings, so the text must be UTF-8 encoded first.

---

## Practical 4: Build a Simple Blockchain in Python

### Aim
To build a simple blockchain in Python by linking blocks using cryptographic hashes and verify chain integrity.

> **Reference File:** Matches your lab notebook `simple_blockchain (1).ipynb` (includes `json.dumps(..., sort_keys=True)`, Proof-of-Work mining with `difficulty`, and 3-step chain integrity validation).

### Simple Step-by-Step Implementation

**Step 1:** Open Google Colab / Jupyter Notebook (or create a file named `exp4_blockchain.py`).  
*(If using your provided `simple_blockchain (1).ipynb` in Colab/Jupyter, simply run all cells in order: **Runtime → Run all**.)*

**Step 2:** Write the following code:

```python
import hashlib
import json
import time

class Block:
    def __init__(self, index, data, previous_hash, timestamp=None, nonce=0):
        self.index = index
        self.timestamp = timestamp or time.time()
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = nonce
        self.hash = self.compute_hash()

    def compute_hash(self):
        """Create a SHA-256 hash of the block's contents."""
        block_string = json.dumps({
            "index": self.index,
            "timestamp": self.timestamp,
            "data": self.data,
            "previous_hash": self.previous_hash,
            "nonce": self.nonce
        }, sort_keys=True)
        return hashlib.sha256(block_string.encode()).hexdigest()

    def __repr__(self):
        return (f"Block #{self.index}\n"
                f"  Timestamp     : {self.timestamp}\n"
                f"  Data          : {self.data}\n"
                f"  Previous Hash : {self.previous_hash}\n"
                f"  Hash          : {self.hash}\n"
                f"  Nonce         : {self.nonce}\n")


class Blockchain:
    def __init__(self, difficulty=2):
        self.difficulty = difficulty          # Number of leading zeros required (simple PoW)
        self.chain = [self.create_genesis_block()]

    def create_genesis_block(self):
        return Block(0, "Genesis Block", "0")

    def get_latest_block(self):
        return self.chain[-1]

    def proof_of_work(self, block):
        """Simple proof-of-work: find a nonce so hash starts with N zeros."""
        target = "0" * self.difficulty
        while not block.hash.startswith(target):
            block.nonce += 1
            block.hash = block.compute_hash()
        return block

    def add_block(self, data):
        previous_block = self.get_latest_block()
        new_block = Block(
            index=previous_block.index + 1,
            data=data,
            previous_hash=previous_block.hash
        )
        new_block = self.proof_of_work(new_block)
        self.chain.append(new_block)
        return new_block

    def is_chain_valid(self):
        """Verify integrity: recompute hashes, check links, and verify PoW difficulty."""
        for i in range(1, len(self.chain)):
            current = self.chain[i]
            previous = self.chain[i - 1]

            # 1. Has this block's own data been tampered with?
            if current.hash != current.compute_hash():
                print(f"Block {current.index} has been tampered with (hash mismatch).")
                return False

            # 2. Does it correctly point to the previous block?
            if current.previous_hash != previous.hash:
                print(f"Block {current.index} is not linked correctly to Block {previous.index}.")
                return False

            # 3. Does it still satisfy the proof-of-work difficulty?
            if not current.hash.startswith("0" * self.difficulty):
                print(f"Block {current.index} does not satisfy proof-of-work difficulty.")
                return False

        return True


def print_chain(blockchain):
    for block in blockchain.chain:
        print(block)


if __name__ == "__main__":
    # 1. Build the chain with Proof-of-Work difficulty = 3 (hash starts with "000")
    my_chain = Blockchain(difficulty=3)
    my_chain.add_block("Alice pays Bob 10 coins")
    my_chain.add_block("Bob pays Charlie 5 coins")
    my_chain.add_block("Charlie pays Dave 2 coins")

    print("===== Blockchain Contents =====\n")
    print_chain(my_chain)

    # 2. Check integrity before tampering
    print("Chain valid?", my_chain.is_chain_valid())

    # 3. Tamper with Block 1 and check again
    print("\nTampering with Block 1 data...\n")
    my_chain.chain[1].data = "Alice pays Bob 1000 coins"
    # Hash is NOT recomputed here, simulating a naive attacker — is_chain_valid() catches it.
    print("Chain valid?", my_chain.is_chain_valid())
```

**Step 3:** Run the notebook (`Runtime → Run all`) or run via terminal:
```bash
python3 exp4_blockchain.py
```

### What to Demonstrate to the Examiner
1. Chain prints Genesis Block (`Block #0`, `Previous Hash : 0`, `Nonce : 0`) followed by mined Blocks `#1`, `#2`, `#3` whose hashes all start with **`000`** (`difficulty=3`) and show their discovered `Nonce` values.
2. Each block's `Previous Hash` matches the exact `Hash` of the block before it.
3. Before tampering: `Chain valid? True`.
4. After changing `my_chain.chain[1].data = "Alice pays Bob 1000 coins"`: outputs `Block 1 has been tampered with (hash mismatch).` and `Chain valid? False`.

### Important Oral / Viva Questions (Practical 4)
1. **What are the three checks performed inside `is_chain_valid()`?**  
   (1) `current.hash != current.compute_hash()` — detects if block data was altered.  
   (2) `current.previous_hash != previous.hash` — detects if the cryptographic link between blocks is broken.  
   (3) `not current.hash.startswith("0" * self.difficulty)` — verifies the block satisfies the Proof-of-Work difficulty target.
2. **Why did we use `json.dumps({...}, sort_keys=True)` in `compute_hash()`?**  
   Sorting keys guarantees a **deterministic JSON string** every time the block is hashed. If keys appeared in a different order, SHA-256 would produce a completely different hash even for identical data.
3. **What is the role of `nonce` and `difficulty` in `proof_of_work()`?**  
   `difficulty` sets how many leading zeros (`"000"` for `difficulty=3`) the hash must start with. `nonce` is incremented repeatedly until `compute_hash()` produces a hash matching that target — making block creation computationally expensive and preventing easy tampering.
4. **What happens if an attacker modifies Block #1 and recalculates its hash?**  
   Even if the attacker recalculates Block #1's hash (and re-mines its PoW nonce), **Block #2** still stores the *old* hash of Block #1 in its `previous_hash` field, so Check #2 catches the broken link. The attacker would have to re-mine Block #1 *and every subsequent block*.
5. **Why does the validation loop start at index `1` instead of `0`?**  
   Because Block `0` is the Genesis Block — it has no previous block (`chain[i - 1]` doesn't exist) and is not mined through `add_block()`.

---

## Practical 5: Key Pair Generation, Message Signing & Verification in Python

### Aim
To generate public/private key pairs and simulate message signing and verification using Python.

### Simple Step-by-Step Implementation

#### Method A (Recommended — Uses `cryptography` with ECDSA `SECP256K1`, the exact curve used by Bitcoin & Ethereum)

**Step 1:** Install the `cryptography` package (one-time):
```bash
pip install cryptography
```

**Step 2:** Create `exp5_digital_signature.py`:
```python
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import ec
from cryptography.exceptions import InvalidSignature

# 1. Generate Private & Public Key Pair (ECDSA - SECP256K1 used in Bitcoin/Ethereum)
private_key = ec.generate_private_key(ec.SECP256K1())
public_key = private_key.public_key()

# Export keys in readable PEM format to display
private_pem = private_key.private_bytes(
    encoding=serialization.Encoding.PEM,
    format=serialization.PrivateFormat.PKCS8,
    encryption_algorithm=serialization.NoEncryption()
)
public_pem = public_key.public_bytes(
    encoding=serialization.Encoding.PEM,
    format=serialization.PublicFormat.SubjectPublicKeyInfo
)

print("=== PRIVATE KEY (Keep Secret!) ===")
print(private_pem.decode())
print("=== PUBLIC KEY (Share Openly) ===")
print(public_pem.decode())

# 2. Sign a Message using the PRIVATE KEY
message = b"Transfer 5 ETH from Alice to Bob"
signature = private_key.sign(message, ec.ECDSA(hashes.SHA256()))
print("Original Message :", message.decode())
print("Digital Signature (hex):", signature.hex(), "\n")

# 3. Verify the Signature using the PUBLIC KEY (Valid Case)
try:
    public_key.verify(signature, message, ec.ECDSA(hashes.SHA256()))
    print("[VALID] Signature verified! Message is authentic and untampered.")
except InvalidSignature:
    print("[INVALID] Signature verification failed!")

# 4. Tamper with the Message and Re-Verify (Invalid Case)
tampered_message = b"Transfer 500 ETH from Alice to Bob"
print("\nTampered Message :", tampered_message.decode())
try:
    public_key.verify(signature, tampered_message, ec.ECDSA(hashes.SHA256()))
    print("[VALID] Signature verified!")
except InvalidSignature:
    print("[INVALID] Tampering detected! Signature does NOT match the tampered message.")
```

**Step 3:** Run it:
```bash
python3 exp5_digital_signature.py
```

#### Method B (Backup — Zero-Dependency Pure Python RSA Simulation)
*Use this ONLY if the lab computer has no internet and `cryptography` is not installed:*

```python
import hashlib

# Small educational RSA parameters (in practice, 2048-bit primes are used)
p, q = 61, 53
n = p * q                     # Modulus = 3233
phi = (p - 1) * (q - 1)       # Totient = 3120
e = 17                        # Public exponent (gcd(e, phi) = 1)
d = pow(e, -1, phi)           # Private exponent (d * e ≡ 1 mod phi)

print(f"Public Key  (e, n): ({e}, {n})")
print(f"Private Key (d, n): ({d}, {n})\n")

def hash_to_int(msg: str) -> int:
    return int(hashlib.sha256(msg.encode()).hexdigest(), 16) % n

def sign(msg: str) -> int:
    # Sign with PRIVATE key d
    return pow(hash_to_int(msg), d, n)

def verify(msg: str, sig: int) -> bool:
    # Verify with PUBLIC key e
    return pow(sig, e, n) == hash_to_int(msg)

message = "Transfer 5 ETH from Alice to Bob"
signature = sign(message)
print(f"Message   : {message}")
print(f"Signature : {signature}")
print("Valid signature check   :", verify(message, signature))

tampered = "Transfer 500 ETH from Alice to Bob"
print("Tampered message check  :", verify(tampered, signature))
```

### Important Oral / Viva Questions (Practical 5)
1. **Which key is used to sign a message, and which key is used to verify it?**  
   **Private key** signs the message; **Public key** verifies the signature. *(Opposite of encryption, where Public encrypts and Private decrypts!)*
2. **What security properties do Digital Signatures provide?**  
   1) **Authentication** (proves who sent it),  
   2) **Integrity** (proves message wasn't altered),  
   3) **Non-repudiation** (sender cannot deny signing it).
3. **Why do we hash the message before signing it?**  
   Asymmetric crypto is slow on large data. Hashing converts any message into a fixed 256-bit digest, making signing fast and secure.
4. **What is ECDSA, and which curve do Bitcoin and Ethereum use?**  
   Elliptic Curve Digital Signature Algorithm. Both Bitcoin and Ethereum use the **`secp256k1`** curve because it gives strong security with much smaller keys (256-bit) compared to RSA (2048–3072-bit).
5. **Can someone derive your private key from your public key?**  
   No. Going from Private → Public is easy (elliptic curve point multiplication), while reversing it (Elliptic Curve Discrete Logarithm Problem) is computationally infeasible.
6. **How is a blockchain wallet address related to keys?**  
   Private Key → Public Key (via ECDSA) → Wallet Address (via hashing the public key, e.g., last 20 bytes of `Keccak-256(public_key)` in Ethereum).

---

## Practical 6: "Hello World" Smart Contract on Remix IDE

### Aim
To write and deploy a basic "Hello World" smart contract on Remix IDE using the Solidity programming language.

### Simple Step-by-Step Implementation

**Step 1: Open Remix IDE**  
Go to https://remix.ethereum.org/ in your browser.

**Step 2: Create Contract File**  
In the left **File Explorer** panel → click the `contracts` folder → click the **New File** icon → name it `HelloWorld.sol`.

**Step 3: Paste the Solidity Code**
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract HelloWorld {
    // State variable stored permanently on the blockchain
    string public message;

    // Constructor executes once during contract deployment
    constructor() {
        message = "Hello, Blockchain World!";
    }

    // State-changing function (costs gas)
    function setMessage(string memory _newMessage) public {
        message = _newMessage;
    }

    // Read-only function (free, no gas when called externally)
    function getMessage() public view returns (string memory) {
        return message;
    }
}
```

**Step 4: Compile the Contract**  
1. Click the **Solidity Compiler** icon (3rd icon on the left sidebar).
2. Make sure Compiler version is `0.8.20` (or any `0.8.x` ≥ `0.8.20`).
3. Click **Compile HelloWorld.sol** → verify the **green checkmark** appears.

**Step 5: Deploy the Contract**  
1. Click the **Deploy & Run Transactions** icon (4th icon on the left sidebar).
2. Set **Environment** to `Remix VM (Cancun)` (or any `Remix VM`).
3. Make sure **Contract** shows `HelloWorld - contracts/HelloWorld.sol`.
4. Click the orange **Deploy** button.

**Step 6: Interact & Verify**  
1. Under **Deployed Contracts** (bottom left), expand `HELLOWORLD`.
2. Click the blue **`getMessage`** button (or **`message`**) → returns `"Hello, Blockchain World!"`.
3. In the orange **`setMessage`** input box, type `"Hello RIT CSE!"` and click **`setMessage`** → notice a transaction runs in the terminal (green checkmark + gas used).
4. Click **`getMessage`** again → returns `"Hello RIT CSE!"`.

### Important Oral / Viva Questions (Practical 6)
1. **What is a Smart Contract?**  
   A self-executing program stored on a blockchain whose code runs automatically on the EVM when predefined conditions are met, without intermediaries.
2. **What does `pragma solidity ^0.8.20;` mean?**  
   It specifies the Solidity compiler version. The caret `^` means any compiler from `0.8.20` up to (but not including) `0.9.0`.
3. **Why is `// SPDX-License-Identifier: MIT` written at the top?**  
   It declares the open-source license of the contract (MIT). Without it, the Solidity compiler raises a warning.
4. **Why are some buttons blue and some orange in Remix IDE?**  
   - **Blue buttons (`view` / `pure`):** Read-only calls. They do not change blockchain state and cost **zero gas**.  
   - **Orange buttons:** State-changing transactions. They modify storage and **cost gas**.  
   - **Red buttons (`payable`):** Functions that can also receive Ether (`ETH`).
5. **What is the difference between `storage`, `memory`, and `calldata` in Solidity?**  
   - `storage`: Permanent state variables stored on the blockchain (expensive).  
   - `memory`: Temporary mutable data during function execution (cheaper).  
   - `calldata`: Temporary read-only function input data (cheapest).
6. **What is the difference between `view` and `pure` functions?**  
   - `view` reads blockchain state variables but does not modify them.  
   - `pure` neither reads nor modifies blockchain state variables (e.g., pure math `a + b`).

---

## Practical 7: Simple Token Transfer Smart Contract on Remix VM

### Aim
To implement a simple token transfer smart contract in Solidity, deploy it on Remix VM, and verify balance changes between accounts.

> **Reference File:** Matches your lab sheet `Exp.7_SimpleToken_Remix.pdf` (minimal ERC-20 style `SimpleToken` / `STK` with `decimals = 18`, `owner`, `balanceOf`, `transfer`, and `getBalance`).

### Simple Step-by-Step Implementation

**Step 1: Open Remix & Create File**  
1. Go to https://remix.ethereum.org/ in your browser.
2. In the **File Explorer**, create a new file named `SimpleToken.sol`.

**Step 2: Paste the Solidity Code**
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract SimpleToken {
    string public name = "SimpleToken";
    string public symbol = "STK";
    uint8 public decimals = 18;
    uint256 public totalSupply;

    address public owner;

    // Maps each Ethereum address to its token balance
    mapping(address => uint256) public balanceOf;

    // Event emitted on minting and every transfer
    event Transfer(address indexed from, address indexed to, uint256 value);

    // Mint initial supply (scaled by 18 decimals) to the deployer
    constructor(uint256 _initialSupply) {
        owner = msg.sender;
        totalSupply = _initialSupply * (10 ** uint256(decimals));
        balanceOf[owner] = totalSupply;
        emit Transfer(address(0), owner, totalSupply);
    }

    // Transfer tokens from caller (msg.sender) to another address
    function transfer(address _to, uint256 _value) public returns (bool success) {
        require(_to != address(0), "Invalid address");
        require(balanceOf[msg.sender] >= _value, "Insufficient balance");

        balanceOf[msg.sender] -= _value;
        balanceOf[_to] += _value;

        emit Transfer(msg.sender, _to, _value);
        return true;
    }

    // Helper to check balance of any account
    function getBalance(address _account) public view returns (uint256) {
        return balanceOf[_account];
    }
}
```

**Step 3: Compile**  
Open the **Solidity Compiler** tab → select compiler version **`0.8.19`** (or any compatible `0.8.x`) → click **Compile SimpleToken.sol** (verify green checkmark).

**Step 4: Deploy on Remix VM**  
1. Open **Deploy & Run Transactions** → set **Environment** to **`Remix VM (Cancun)`** (provides test accounts pre-loaded with fake ETH).
2. Ensure **Account 0** is selected in the `ACCOUNT` dropdown (this becomes `owner` and receives all initial tokens).
3. Select the **`SimpleToken`** contract → enter constructor argument `_initialSupply`: **`1000`** → click **Deploy**.

**Step 5: Verify Balance Changes Between Accounts**  
1. **Check Initial Balances:**
   - Expand `SIMPLETOKEN` under **Deployed Contracts**.
   - Call `getBalance(Account0_address)` → returns **`1000000000000000000000`** (`1000 STK`, scaled by 18 decimals).
   - Switch `ACCOUNT` dropdown to **Account 1** to copy Account 1's address, then **switch back to Account 0** (since Account 0 is `msg.sender` and owns the tokens!).
   - Call `getBalance(Account1_address)` → returns **`0`**.
2. **Perform a Transfer (100 STK):**
   - Keep **Account 0** selected as the active account.
   - Expand **`transfer`** and enter:
     - `_to`: Account 1's address
     - `_value`: **`100000000000000000000`** *(100 followed by 18 zeros = 100 STK)*
   - Click **transact**.
3. **Verify Updated Balances & Event Logs:**
   - Call `getBalance` for both accounts again:

     | Account | Balance Before | Balance After | Raw Value (18 decimals) |
     | :--- | :--- | :--- | :--- |
     | **Account 0 (sender)** | `1000 STK` | **`900 STK`** | `900000000000000000000` |
     | **Account 1 (receiver)** | `0 STK` | **`100 STK`** | `100000000000000000000` |

   - Expand the transaction in the Remix console → inspect the **`logs`** section to show the emitted **`Transfer`** event (`from`, `to`, `value`).
4. **Negative Test Case (Recommended for Full Marks!):**
   - Try transferring more tokens than Account 0's balance (e.g., `2000000000000000000000`) → Remix reverts the transaction with **`"Insufficient balance"`**.

### Important Oral / Viva Questions (Practical 7)
1. **Why does the contract use `decimals = 18` and multiply `_initialSupply * (10 ** uint256(decimals))`?**  
   Solidity does **not** support floating-point numbers (`float`/`double`). To represent fractional tokens (like `0.5 STK`), token amounts are stored as integers in their smallest unit (just like `1 ETH = 10^18 Wei`), so `100 STK` is passed as `100000000000000000000`.
2. **Why does the constructor emit `Transfer(address(0), owner, totalSupply)`?**  
   In the ERC-20 standard, emitting a `Transfer` event *from* the zero address (`0x000...000`) signals **minting** — creating new tokens and assigning them to `owner`.
3. **What is `msg.sender` in Solidity?**  
   A global variable containing the Ethereum address of the account (or contract) that directly called the current function. In the constructor, `owner = msg.sender` sets the deployer as the owner.
4. **What is a `mapping` in Solidity?**  
   A key-value hash table (like a Python dictionary). Here `mapping(address => uint256) public balanceOf` maps each wallet address to its token balance. Unset keys default to `0`.
5. **What does `require()` do when the condition is false?**  
   It immediately **reverts** the transaction, undoes all state changes, refunds unused gas, and returns the error message (e.g., `"Invalid address"` or `"Insufficient balance"`).
6. **What is an `event`, and what does `indexed` do?**  
   Events write structured logs into the transaction receipt (cheaper than storage) so DApps and Etherscan can track transfers. Marking `from` and `to` as `indexed` allows fast filtering/searching by address (up to 3 indexed parameters per event).
7. **What is ERC-20?**  
   The official Ethereum standard for **fungible tokens** (every token is identical and interchangeable), defining standard functions like `totalSupply`, `balanceOf`, `transfer`, `approve`, `transferFrom`, and `allowance`.
8. **Why do we check `require(_to != address(0), "Invalid address")`?**  
   `0x0000...0000` is the burn/null address. Any tokens sent there are permanently lost and unrecoverable.

---

## Practical 8: Deploy on Ethereum Sepolia Testnet & Verify on Etherscan

### Aim
To deploy a smart contract on the Ethereum Sepolia testnet using MetaMask and verify the transaction on Etherscan.

### Simple Step-by-Step Implementation

**Step 1: Prepare MetaMask on Sepolia Testnet**  
1. Open the **MetaMask** browser extension and unlock it.
2. Click the **Network dropdown** (top-left) → toggle ON **Show test networks** → select **Sepolia**.
3. Make sure your account has test ETH (e.g., `0.05 SepoliaETH`). If `0`, copy your MetaMask address and claim free test ETH from a Sepolia faucet (e.g., Google Cloud Web3 Faucet or Alchemy Faucet).

**Step 2: Compile Your Smart Contract in Remix**  
1. Open https://remix.ethereum.org/ and open `HelloWorld.sol` (from Practical 6) or `SimpleToken.sol` (from Practical 7).
2. Compile it in **Solidity Compiler** (ensure green checkmark).

**Step 3: Connect Remix to MetaMask**  
1. Go to **Deploy & Run Transactions**.
2. Change **Environment** from `Remix VM` to **`Injected Provider - MetaMask`**.
3. A MetaMask popup will ask to connect → select your account → click **Next → Connect**.
4. Verify Remix now displays: **`Sepolia (11155111) network`** and your MetaMask wallet address + SepoliaETH balance.

**Step 4: Deploy to Sepolia Testnet**  
1. Click the orange **Deploy** button (if deploying `SimpleToken`, enter `1000` as `_initialSupply`).
2. MetaMask pops up showing **Estimated Gas Fee** → click **Confirm**.
3. Wait **12–15 seconds** for the transaction to be included in a Sepolia block.
4. Once confirmed, the Remix terminal shows a green checkmark with a **"view on etherscan"** link, plus the deployed contract appears under **Deployed Contracts**.

**Step 5: Verify the Transaction on Sepolia Etherscan**  
1. Copy the **Transaction Hash** (or click **"view on etherscan"** in Remix terminal).
2. Open https://sepolia.etherscan.io/ and paste the Transaction Hash in the search bar.
3. Show the examiner the following details on Etherscan:
   - **Transaction Hash:** Unique ID of your deployment tx.
   - **Status:** `Success` (green badge).
   - **Block:** The Sepolia block number that mined your transaction.
   - **From:** Your MetaMask wallet address.
   - **To:** `[Contract 0x... Created]` — click this to view your deployed contract page!
   - **Transaction Fee & Gas Used:** Amount of SepoliaETH paid in gas.

**Step 6 (Bonus — Impress the Examiner!):**  
1. Call `setMessage("Deployed on Sepolia!")` from Remix → Confirm in MetaMask.
2. Refresh your Contract page on Sepolia Etherscan → show the **2nd transaction (`Set Message`)** listed live on-chain!

### Important Oral / Viva Questions (Practical 8)
1. **What is the difference between Ethereum Mainnet and a Testnet (like Sepolia)?**  
   Mainnet uses real ETH with real monetary value. Testnets (like Sepolia, Chain ID `11155111`) mimic Mainnet behavior using free test ETH so developers can test contracts safely without risking money.
2. **What is MetaMask?**  
   A non-custodial browser/mobile crypto wallet that manages private keys, signs transactions, and injects a Web3 provider (`window.ethereum`) so DApps like Remix can talk to Ethereum networks.
3. **What is "Injected Provider - MetaMask" in Remix?**  
   Instead of running a fake local blockchain inside the browser (`Remix VM`), Remix sends transactions through MetaMask's injected provider to an actual Ethereum network (Sepolia).
4. **What is Gas, Gas Price, and Gas Limit?**  
   - **Gas:** Unit measuring computational work on the EVM.  
   - **Gas Price:** Amount of ETH (in **Gwei**) paid per unit of gas.  
   - **Gas Limit:** Maximum gas the sender is willing to spend on a transaction.  
   - **Transaction Fee** = `Gas Used × Effective Gas Price`.
5. **What is Etherscan?**  
   A blockchain explorer and analytics platform for Ethereum that lets anyone inspect transactions, blocks, wallet balances, gas fees, and smart contract source code.
6. **What is a Faucet?**  
   A web service that dispenses small amounts of free testnet tokens (like SepoliaETH) to developers for testing.
7. **What are ABI and Bytecode when compiling a smart contract?**  
   - **Bytecode:** Low-level machine code actually deployed and executed on the EVM.  
   - **ABI (Application Binary Interface):** JSON specification describing the contract's functions and parameters so frontends/wallets know how to interact with it.

---

## Rapid-Fire General Viva Questions (Cheat Sheet)

| Question | Short & Crisp Answer |
| :--- | :--- |
| **What is the EVM?** | **Ethereum Virtual Machine** — the decentralized sandbox runtime that executes Solidity smart contract bytecode across all Ethereum nodes. |
| **Units of Ether?** | `1 Ether = 10^9 Gwei = 10^18 Wei`. (Wei is the smallest unit; gas prices are quoted in Gwei.) |
| **EOA vs Contract Account?** | **EOA** (Externally Owned Account) is controlled by a private key (MetaMask) and can initiate transactions. **Contract Account** is controlled by code and has no private key. |
| **Hot Wallet vs Cold Wallet?** | **Hot wallet** is connected to the internet (MetaMask — convenient). **Cold wallet** is offline hardware/paper storage (Ledger/Trezor — highest security). |
| **Soft Fork vs Hard Fork?** | **Soft fork** is backward-compatible (old nodes still accept new blocks). **Hard fork** is NOT backward-compatible and splits the chain if nodes don't upgrade (e.g., ETH vs ETC). |
| **Web 1.0 vs Web 2.0 vs Web 3.0?** | Web 1.0 = Read-only (static pages); Web 2.0 = Read-Write (centralized platforms); Web 3.0 = Read-Write-Own (decentralized, blockchain-based). |
| **What is a Seed Phrase (Mnemonic)?** | 12 or 24 human-readable words (BIP-39) used to back up and recover all private keys in a wallet. Never share it! |
| **What is Finality?** | The guarantee that once a transaction is confirmed in a block, it cannot be altered or reversed. |
