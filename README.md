# 🚀 Soroban Atomic Swap Smart Contract

This project is a simple **Atomic Swap** smart contract

## 🧩 Features

- **Atomic swap** between two participants (A and B)
- **Both sides must approve** the swap (auth checks)
- **Minimum amount protection** for both tokens
- **Partial refund logic**: if max spend > swap amount, excess is refunded
- **Fully unit-tested** with mocked authorizations

## 📂 Project Structure

- `src/lib.rs`: Main smart contract logic
- `src/test.rs`: Unit tests covering swap execution and authorization flow

## ⚙️ How It Works

1. Both users approve (authorize) the swap.
2. Contract pulls tokens from both users into itself.
3. Contract redistributes swapped tokens back to the users.
4. Any **overpaid** amount is refunded to the original owners.

✅ Either **both sides succeed**, or **nothing happens** = **atomicity** guaranteed.

## 📜 Example Scenario

- User A swaps 1000 TokenA for at least 4500 TokenB.
- User B swaps 5000 TokenB for at least 950 TokenA.
- After the swap:
  - A receives 4500 TokenB.
  - B receives 950 TokenA.
  - Excess tokens (50 TokenA, 500 TokenB) stay with original owners.

## 🚀 Getting Started

Make sure you have [Rust](https://rustup.rs/) and Soroban CLI installed.

```bash
# Clone the repository
git clone https://github.com/DenizOk20/atomic-swap.git
cd atomic-swap

# Run the tests
cargo test
```
