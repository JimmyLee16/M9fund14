# App UX/UI

### ⚙️ Technical Architecture

#### 1. **Frontend**

* **Framework**: SvelteKit / React (TBD)
* **Wallet integration**: Custom connector using Midnight's wallet stub (or CIP-95-like abstraction if available)
* **ZK interaction**: Frontend generates ZK proofs (commit/reveal) using browser-based cryptographic tools (e.g., snarkjs, wasm bindings)
* **State machine**:
  * Proposal List → Proposal Detail → Vote → Commit Stage → Reveal Stage → Result View

#### 2. **Smart Contract Layer**

* **Platform**: Midnight testnet
* **Contract Types**:
  * `ProposalContract`: defines proposal metadata and state
  * `VoteSessionContract`: manages commit/reveal cycle
  * `VoterIdentity`: ephemeral identity generation per vote (e.g., via nullifier/secret)
* **Privacy Mechanism**: ZK-SNARK-based commit-reveal (e.g., using hash(secret, proposal\_id))

#### 3. **Data Model**

* **Proposal**
  * ID, title, description, start/end time
* **VoteCommit**
  * Proposal ID, commitment hash, nullifier
* **VoteReveal**
  * Proposal ID, secret, vote choice, proof
* **Tally**
  * Aggregated result (revealed + verified)

***

### 🖥️ UI Screens & UX Flow

| Screen                     | Purpose                                | Notes                                      |
| -------------------------- | -------------------------------------- | ------------------------------------------ |
| 🏠 **Home / DAO Overview** | View list of proposals, DAO profile    | Includes proposal status (open/closed)     |
| 📄 **Proposal Detail**     | See full description, choices          | Proposal metadata, voting rules            |
| ✅ **Vote - Commit**        | User selects choice, creates ZK commit | No vote revealed yet; generates hash       |
| 🔐 **Vote - Reveal**       | User submits proof + secret            | Validates vote, adds to tally              |
| 📊 **Results**             | Anonymous tally result                 | Only revealed votes shown                  |
| ⚙️ **Admin (optional)**    | For DAO project managers               | To create proposals, manage voting windows |

***

### 🧩 Security & Privacy Considerations

* **No on-chain identity leakage**: Voter addresses are never linked to choices
* **One-vote-per-user enforcement**: Nullifier-based or epoch-limited voting
* **Frontend warnings for timing**: UI guides user when to commit vs reveal
* **Client-side validation**: ZK proof generation occurs locally
