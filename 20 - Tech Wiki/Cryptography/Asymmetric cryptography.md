## Definition

- **Asymmetric cryptography** (also called **public-key cryptography**) is a family of cryptographic techniques where each user has a [[Private & Public keys pair]]:
  - a **private key** (kept secret)
  - a **public key** (shared publicly)
- What makes it “asymmetric” is that **different keys are used for different operations** (unlike symmetric cryptography where the same secret key is shared).

## The key pair (private key vs public key)

- **Private key**:
  - must remain secret (anyone who gets it can impersonate you)
  - used to **sign** messages/transactions (and sometimes to decrypt, depending on the scheme)
- **Public key**:
  - can be shared safely
  - used to **verify** signatures (and sometimes to encrypt, depending on the scheme)

## The 2 main use cases

### 1) Encryption (confidentiality)

- Goal: **only the intended recipient can read the message**.
- Typical flow:
  - Alice encrypts a message using **Bob’s public key**.
  - Bob decrypts it using **Bob’s private key**.
- In practice, asymmetric encryption is often used in a **hybrid** way:
  - use asymmetric crypto to securely share a random **symmetric key**
  - then use that symmetric key to encrypt the actual data (faster for large messages)

### 2) Digital signatures (authenticity + integrity)

- Goal: prove **who** created a message and that it **was not altered**.
- Typical flow:
  - Alice creates a signature using **Alice’s private key**.
  - Anyone can verify the signature using **Alice’s public key**.
- Most systems sign a **hash of the message** rather than the whole message directly (see [[Hash]]).
## Why it matters in blockchains

- In Ethereum and many other chains, asymmetric cryptography is primarily used for **digital signatures**:
  - you sign a transaction with your **private key**
  - the network verifies it with your **public key**
  - this proves you are authorized to spend from that address
- This is the foundation of wallet ownership: a wallet is essentially a [[Private & Public keys pair]].

## Security intuition (why it works)

- Asymmetric cryptography relies on “easy to do, hard to reverse” math problems:
  - **RSA**: hard to factor large integers
  - **Elliptic curves (ECDSA/ECDH/Ed25519 family)**: hard to solve the elliptic curve discrete logarithm problem
- Security depends heavily on:
  - key size / curve choice
  - correct implementations
  - protecting the private key (often the weakest link)

## Quick mental model (Alice/Bob example)

- **Signing**:
  - Alice signs “I authorize this transaction” with her private key.
  - Everyone verifies the signature with Alice’s public key.
- **Encryption**:
  - Alice encrypts a message with Bob’s public key.
  - Only Bob can decrypt it with Bob’s private key.
