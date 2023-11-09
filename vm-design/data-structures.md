# Data Structures for Virtual Machine (VM)

## Table of Contents

1. [Introduction](#introduction)
2. [Stack](#stack)
3. [Memory](#memory)
4. [Storage Model](#storage-model)
5. [State](#state)
6. [Considerations for Data Structures](#general-considerations-for-data-structures)

## Introduction

When designing data structures for a Virtual Machine (VM), particularly for a blockchain context, we must ensure that they are efficient, secure, and scalable. Below we finalize the specifications for the Stack, Memory, Storage Model, and State of the VM.

## Stack

- **Description**: The Stack is a Last-In-First-Out (LIFO) data structure used for holding temporary variables during the execution of instructions.
- **Maximum Size**: The stack should have a predefined maximum size to prevent stack overflow. A typical size could be 1024 elements.
- **What it is**: A stack of plates in a cafeteria.
- **Example**: If you need to use a plate, you take one from the top. When cleaning up, you place it back on top. This is the "Last-In-First-Out" system.
- **Operations**:
  - `PUSH`: Adding a new plate to the stack. Add an item to the top of the stack.
  - `POP`: Taking the top plate off to use. Remove the top item from the stack.
  - `PEEK`: Looking at the top plate without removing it. Read the top item from the stack without removing it.
  - `DUP`: Getting a new plate exactly like the top one. Duplicate the top item on the stack.
  - `SWAP`: Exchanging the top two plates. Swap the top two items on the stack.

## Memory

- **Description**: Memory is a byte-addressable space where each byte can be read and written.
- **Allocation**: Memory is dynamically expanded by instructions that write to it. There is no need to preallocate memory.
- **Access**: Memory can be accessed via `LOAD` and `STORE` instructions that read and write respectively.
- **Cleanup**: Memory is volatile and its contents are lost after transaction execution.
- **What it is**: A series of mailboxes lined up on a street.
- **Example**: A smart contract, like a person writing notes, puts these in mailboxes (memory) and retrieves them when necessary.
- **Operations**:
  - `LOAD`: Checking what's inside a mailbox.
  - `STORE`: Putting a note into a mailbox.

## Storage Model

- **Description**: Storage is a key-value store that persists across transactions.
- **Key-Value Store**: Storage entries are accessed via unique keys, and the value is the data associated with that key.
- **Access Patterns**:
  - `SLOAD`: Read data from storage using a key.
  - `SSTORE`: Write data to storage with a key.
- **Persistence**: Data in storage remains persistent across different executions and transactions.
- **What it is**: A filing cabinet in an office.
- **Example**: A smart contract's storage is like a file in a cabinet, holding important documents like membership lists that persist over time.
- **Operations**:
  - `SLOAD`: Finding and reading a particular file.
  - `SSTORE`: Adding or updating a file in the cabinet.

## State

- **Components**:
  - **Account Balances**: Each account's balance.
  - **Nonces**: A counter used to ensure each transaction can only be processed once.
  - **Contract Code**: The bytecode associated with a given contract.
  - **Contract Storage**: The persistent storage of key-value pairs associated with a contract.
- **State Transition**: The state transition function applies transactions to the current state to produce a new state.
- **What it is**: The complete ledger of a bank.
- **Example**: The state represents all the accounts, balances, and contracts—like the bank ledger holding records of every account and transaction.
- **Components**:
  - **Account Balances**: The amount of money each person has in the bank.
  - **Nonces**: Unique identifiers for each transaction, similar to check numbers.
  - **Contract Code**: The set of rules or agreements of a club, written and stored securely.
  - **Contract Storage**: Permanent records like the club's membership list or meeting minutes.

## General Considerations for Data Structures

- **Efficiency**: Data structures are optimized for the most frequent operations, ensuring quick and reliable access. The VM works like a well-organized kitchen, letting the chef (the smart contract) work quickly and effectively.
- **Security**: The data structures are secured like a warehouse with locks and surveillance to prevent theft or tampering.
  - Stack operations ensure that stack underflows and overflows are checked and handled.
  - Memory accesses are bounds-checked to prevent unauthorized access.
  - Storage accesses are authenticated, ensuring only the owning contract can modify its storage.
- **Scalability**: The structures can expand like a library, able to add more books to its collection without running out of space.
  - The stack has a maximum size to prevent certain types of attacks and ensure scalability.
  - Memory is expandable but is cleaned up after execution to prevent excessive growth.
  - Storage is designed to grow as needed but is kept efficient through techniques such as Patricia trees.

These data structures and their operations are critical to the VM's function, allowing it to execute complex tasks while maintaining the blockchain network's integrity. They are robust and secure, designed to operate effectively under a wide range of conditions and demands.
