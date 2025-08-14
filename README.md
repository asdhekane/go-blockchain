# Building a Blockchain in Go

This project is a simple, educational implementation of a blockchain built in the Go programming language. It is based on the tutorial series "Building Blockchain in Go" by Ivan Ivanov.

This repository currently covers the concepts and features from the first three parts of the series:
* **Part 1: Basic Prototype**
* **Part 2: Proof of Work**
* **Part 3: Persistence and CLI**

## Features Implemented

* **Core Blockchain Structure:** A chain of linked blocks, where each block contains its own hash, the hash of the previous block, and data.
* **Proof-of-Work Consensus:** Secures the blockchain by requiring computational effort (mining) to add new blocks. This prevents malicious actors from easily altering the chain.
* **Data Persistence:** The blockchain is stored in a local key/value database ([BoltDB](https://github.com/boltdb/bolt)) to ensure data survives between application runs.
* **Command-Line Interface (CLI):** Provides a simple interface to interact with the blockchain, allowing users to add new blocks and print the chain's contents.

## Tech Stack

* **Language:** [Go](https://golang.org/)
* **Database:** [BoltDB](https://github.com/boltdb/bolt) (an embedded key/value database)

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine.

### Prerequisites

You must have Go installed on your system. You can download it from the [official Go website](https://golang.org/dl/).

### Installation & Build

1.  **Clone the repository:**
    ```sh
    git clone <your-repository-url>
    cd <repository-name>
    ```

2.  **Tidy dependencies:**
    Go will automatically handle the dependencies (like BoltDB) when you build or run the project. You can manually tidy them if you wish:
    ```sh
    go mod tidy
    ```

3.  **Build the executable:**
    Compile the source code to create an executable file.
    ```sh
    go build -o blockchain-cli .
    ```

## Usage

This project uses a command-line interface to interact with the blockchain. Once you have built the executable (`blockchain-cli`), you can use the following commands.

**1. Create a new blockchain:**

The first command you run must be to create the blockchain. This will generate a `blockchain.db` file.

```sh
./blockchain-cli createblockchain
```

**2. Add a new block:**

To add a new block to the chain with some data:
```sh
./blockchain-cli addblock -data "Your data here"
```
*(Replace "Your data here" with any string you want to store in the block.)*

**3. Print the blockchain:**

To display all the blocks currently in the chain, along with their data and proof-of-work information:
```sh
./blockchain-cli printchain
```

## Core Concepts Covered

* **Blocks & Hashing:** The fundamental building blocks of the chain. Each block is uniquely identified and secured by a cryptographic hash (SHA-256).
* **Proof-of-Work (PoW):** A consensus algorithm that introduces a computational challenge (mining) to the block creation process. A block is only considered valid if its hash meets a certain difficulty target (i.e., starts with a specific number of zeros).
* **Persistence with BoltDB:** The blockchain data is stored in a BoltDB database file. This allows the chain's state to be saved and loaded, making it persistent.
* **CLI Interaction:** A simple command-line interface built using Go's `flag` package allows for user interaction with the blockchain's core functions.
