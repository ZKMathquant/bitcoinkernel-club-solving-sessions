# Session 1: Introduction to Bitcoinkernel & C API Basics

## Overview

The kernel library supports three fundamental features:

1. **"Context-free" validation** - Validates data structures with a subset of Bitcoin Core rules, without reading/writing from disk
2. **Full validation** - Applies complete validation rules including block processing, reads/writes from/to disk
3. **Bitcoin Core data retrieval** - Iterates over indexed blocks and reads them from disk

Though these examples use the C API, users from other programming languages should use wrappers for their respective languages, which often provide simplified and more ergonomic interfaces with less manual memory management.

## Getting Started

1. Enter the session shell:
```bash
nix develop .#session1
```

2. Compile the code:
```bash
make
```

3. Run the program:
```bash
make run
```

## Context-Free Validation

This session focuses on **context-free validation** - validation functions that don't require you to explicitly instantiate a `btck_Context`. These functions validate data structures with a subset of the full Bitcoin Core rules and don't read or write data from/to disk.

Currently, this includes **script validation**.

### Why Context-Free?

The user doesn't need to:
- Set up callbacks
- Create stateful infrastructure
- Have access to blockchain data files
- Manage complex chainstate

This makes context-free validation perfect for:
- Validating individual scripts
- Testing transaction validity without full chain context
- Learning the bitcoinkernel API basics

## Your Task

The provided `src/main.c` implements a **Taproot transaction validation** example. It validates a spend of a taproot output using context-free script validation.

You'll learn:
- How to create transaction and script pubkey objects
- How to verify script pubkeys against transactions
- How to properly manage memory and clean up resources

## Resources

- [PR #30595](https://github.com/bitcoin/bitcoin/pull/30595)
- [bitcoinkernel.h](https://github.com/bitcoin/bitcoin/blob/master/src/kernel/bitcoinkernel.h)

## Additional Validation Types (Future Sessions)

## What You'll Learn

In this session's example, you'll see:

1. **Transaction creation** from raw bytes
2. **Script pubkey creation** from script data
3. **Transaction output creation** with amount and script pubkey
4. **Script verification** with proper flags and status checking
5. **Memory management** with proper cleanup of all resources

The example validates a real Taproot transaction (`33e794d097969002ee05d336686fc03c9e15a597c1b9827669460fac98799036`) spending a P2TR output.