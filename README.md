
# 📊 Decentralized Voting System

A smart contract for creating, managing, and securely casting votes in elections on the blockchain. Built with [Clarity](https://docs.stacks.co/write-smart-contracts/clarity), this system enables transparent, verifiable voting with built-in protections against fraud, tampering, and double voting.

---

##  Features

* **Create Elections**: Anyone can create an election with a title, description, timeline, and voting options.
* **Activate/End Elections**: Only the election creator or contract owner can activate or prematurely end an election.
* **Secure Voting**: Only one vote per user per election. Options are validated and timestamped.
* **Real-Time Results**: Vote counts are tracked and publicly viewable.
* **Tamper-Proof**: All election data is stored immutably on-chain.

---

##  How It Works

### Election Lifecycle

1. **Create Election**
   Creator defines the election title, description, start & end times, and a list of options.
2. **Activate Election**
   Election must be activated before voting begins.
3. **Cast Votes**
   Users vote for a valid option during the active period.
4. **End Election**
   The creator or contract owner can end the election early; otherwise it ends automatically after the set time.

### Voting Logic

* Each vote is:

  * Validated against the list of options
  * Recorded with a timestamp
  * Counted towards the total
  * Tracked per user to prevent double-voting

---

##  Contract Structure

### Constants

* `contract-owner`: Creator of the contract.
* Custom error codes (`err-owner-only`, `err-already-voted`, etc.)

### Data Structures

* **Maps**:

  * `elections`: Metadata and options for each election
  * `election-results`: Vote tally for each option
  * `user-votes`: Records of user participation
  * `election-voters`: List of voters for an election
* **Vars**:

  * `next-election-id`: Tracks the next available election ID

---

##  Public Functions

| Function            | Description                                      |
| ------------------- | ------------------------------------------------ |
| `create-election`   | Initialize a new election with options           |
| `activate-election` | Starts an election (only by creator or owner)    |
| `end-election`      | Ends an active election early                    |
| `cast-vote`         | Vote for a specific option in an active election |
| `get-election`      | Retrieves election details (partial code shown)  |

---

##  Security & Access Control

* Only the **contract owner** or **election creator** can activate or end elections.
* Double voting is prevented by tracking user participation.
* Voting is restricted to the **active period** only.
* Invalid option IDs are rejected with strict checking.

---

## ✅ Requirements

* Stacks blockchain
* Clarity smart contract environment (e.g., Clarinet or Hiro Web IDE)

---

##  Testing

To test the smart contract:

1. Use [Clarinet](https://docs.stacks.co/clarity/clarinet) to run unit tests
2. Deploy to a testnet
3. Simulate election creation and user voting
4. Query vote counts and validate voter access rules

---

##  Use Cases

* DAO proposal voting
* Decentralized governance
* On-chain community decisions
* Transparent opinion polls
