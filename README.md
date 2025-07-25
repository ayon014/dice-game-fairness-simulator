# 🎲 Fair Dice Game

A cryptographic dice simulation game that ensures **provable fairness** between two players using **HMAC commitments** and **collaborative randomness generation**.

---

## 🚀 Features

- ✅ **Cryptographic Fairness** – Secure HMAC commitments prevent cheating.
- 🤝 **Collaborative Randomness** – Both computer and user contribute to randomness.
- 📊 **Probability Analysis** – Shows win rates between all dice pairs in a table.
- 🧩 **Modular Design** – Structured with multiple classes, each with a single responsibility.
- 🛡️ **Robust Input Handling** – Ensures user inputs are valid and secure.

---

## 🕹️ Game Rules

1. The game starts with a **probability table** showing the win rate between each pair of dice.
2. A **fair coin flip** (using cryptographic commitment) decides who picks first.
3. The first player selects a die.
4. The second player picks from the remaining dice.
5. Both players roll their dice collaboratively:
   - The computer **commits to a secret** using HMAC.
   - The user provides a **random seed**.
   - Final roll is computed by combining both inputs.
6. The player with the **higher roll wins**.

---

## 🔐 Technical Implementation

### Cryptographic Fairness

- **First-Move Determination** – The computer commits to a secret bit using HMAC.
- **Dice Rolling** – Computer commits to a secret seed; user provides a random number.
- **HMAC Verification** – All commitments are fully verifiable after reveal.

---

## 🧱 Classes Overview

| Class              | Responsibility                                      |
|--------------------|------------------------------------------------------|
| `Die`              | Represents a single die with 6 faces                |
| `DiceParser`       | Parses command-line arguments into dice objects     |
| `ProbabilityTable` | Displays win probabilities for all dice combinations|
| `DieSelector`      | Handles die selection logic for both players        |
| `DieRoller`        | Conducts the collaborative dice rolling             |
| `FairnessMechanism`| Ensures provable fairness in coin flip              |
| `InputHandler`     | Manages input validation and user prompts           |
| `DiceGame`         | Main controller class for game flow                 |

---

## 📦 Installation & Usage

Dependencies:

cli-table3 – For clean and elegant console tables.

js-sha3 – For computing SHA3-256 and HMAC hashes.

```bash
# Install dependencies
npm install cli-table3 js-sha3

# Run with custom dice (each die has 6 comma-separated faces)

node main.js 1,2,3,4,5,6 1,3,5,7,9,5 2,2,4,4,6,6
