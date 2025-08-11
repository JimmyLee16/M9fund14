---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Proposal 2 -  SDK

## 🛠️ Midnight DAO Voting SDK

This document provides a **production-ready SDK** for integrating **anonymous voting** into DAO applications using the [Midnight](https://midnight.network) privacy sidechain on Cardano.

### 🎯 Purpose

To deliver a modular, developer-friendly SDK enabling:

* Anonymous voting lifecycle (proposal → ballot → result)
* CLI tooling and mock testing support
* Integration-ready architecture for privacy DAO dApps

### 🧱 Core Modules

* `vote-core`: Core logic handling voting stages and data flow
* `vote-test-env`: Configurable mock testnet simulation
* `vote-cli`: Command-line interface for developers
* `vote-docs`: Full technical documentation & integration guide

### 📁 Folder Structure

```
/vote-core       → business logic  
/vote-test-env   → mock config, testing presets  
/vote-cli        → CLI interface  
/vote-docs       → documentation & usage  
```

### 🚀 Use Cases

* DAO builders on Cardano looking to integrate private governance
* Midnight-based ZK voting flow implementations
* Education and research on privacy-preserving coordination

### 📌 Status

✅ Actively maintained\
🔧 Built with production integration in mind\
📖 Full documentation and test cases included

### 📬 Contact

For collaboration or support, please contact the SDK team.
