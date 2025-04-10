# stdlib.func: The Standard Library for FunC

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

`stdlib.func` is a foundational standard library designed for smart contract development in FunC on The Open Network (TON). It aims to provide a robust set of commonly used, well-tested, and efficient building blocks, simplifying development and promoting code reuse across various TON projects.

This library covers fundamental operations ranging from basic data structure manipulation (BoC, Tuples, Dictionaries) and cryptographic functions to blockchain interactions and adherence to common TON Enhancement Proposals (TEPs).

## Features

This library provides a wide array of functionalities grouped into logical modules:

*   **Blockchain Interaction (`blockchain.func`):** Functions for interacting with the blockchain environment, including gas management, time retrieval, balance checking, address manipulation, and accessing configuration parameters.
*   **Data Serialization/Deserialization (`boc.func`):** Primitives for working with TON's Bag of Cells (BoC) format, including creating cells with `builder` objects and parsing cells using `slice` objects. Covers integer types, references, optional values, and more.
*   **Cryptographic Operations (`crypto.func`):** Essential cryptographic functions like cell/slice hashing (including SHA256) and signature verification (Ed25519, Secp256r1, BLS).
*   **Dictionaries (`dict.func`):** Comprehensive support for TON's HashmapE (dictionary) data structure, including creation, get/set/add/replace/delete operations, iteration, prefix operations, and handling different key/value types (slice, cell, integer, builder).
*   **Mathematical Utilities (`math.func`):** Basic integer arithmetic helper functions like min, max, and absolute value.
*   **Message Handling (`msg.func`):** Primitives for parsing and constructing message addresses (standard, variable, external), handling message flags (bounceable/non-bounceable), and working with message components like opcodes and query IDs. Includes constants for standard send modes.
*   **Common Standards (`standards.func`):** Constants for standard operation codes (op::*) defined in various TEPs (e.g., TEP-62 NFT, TEP-74 Jetton, TEP-85 SBT) and utilities for token metadata handling (TEP-64).
*   **Tuple/List Manipulation (`tuples.func`):** Functions for creating, accessing, and manipulating tuples, including support for Lisp-style lists using nested pairs.

## Repository Structure

The library is organized into several `.func` files, each focusing on a specific domain:

```
stdlib.func/
├── LICENSE           # MIT License file
├── README.md         # This file
├── blockchain.func   # Blockchain interaction primitives
├── boc.func          # Cell, Slice, Builder operations (Bag of Cells)
├── crypto.func       # Hashing and signature verification
├── dict.func         # Dictionary (HashmapE) operations
├── lib.func          # Main include file, aggregates other modules
├── math.func         # Basic mathematical utilities
├── msg.func          # Message parsing, address handling, send modes
├── standards.func    # Standard opcodes (TEPs) and metadata constants
└── tuples.func       # Tuple and Lisp-style list manipulation
```

The `lib.func` file simply includes all other modules, providing a single entry point for using the entire standard library.

## Installation

It is recommended to add this repository as a submodule to your smart contract project, particularly if you are using frameworks like Blueprint.

**Using Blueprint:**

Execute the following command in your project's root directory to add `stdlib.func` as a submodule into the standard imports directory:

```bash
git submodule add https://github.com/pyAndr3w/stdlib.func.git contracts/imports/std
```

This command clones the repository into `contracts/imports/std`.


## Usage

To use the standard library functions in your FunC smart contract code, include the main library file:

```func
#include "imports/std/lib.func";

;; Your smart contract code here
```

The `#include "imports/std/lib.func";` directive makes all functions defined across the different modules (`boc.func`, `dict.func`, etc.) available for use in your contract. The path assumes you followed the recommended installation structure for Blueprint. Adjust the path if your project structure differs.

While you *can* include individual `.func` files if you only need specific functionality, including `lib.func` is the standard and recommended approach.

## API Documentation

The detailed documentation for each function, including its purpose, arguments (`Args:`), and return values (`Returns:`), is provided directly within the respective `.func` files as comments preceding the function definition (using `;;;` markers). Please refer to the source files for specific function details.

## Contributing

Contributions are welcome! If you find a bug, have a feature request, or want to improve the library or its documentation, please feel free to:

1.  Open an issue on the repository's issue tracker.
2.  Fork the repository, make your changes, and submit a pull request.

Please try to adhere to the existing coding style and documentation standards.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.