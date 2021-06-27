```
LNPBP: 0007
Layer: Client-validated data (3)
Vertical: Consensus layer
Title: Strict encoding formal semantics and notation syntax (SE/1)
Authors: Dr Maxim Orlovsky <orlovsky@protonmail.ch>,
         Peter Todd,
Comments-URI: <https://github.com/LNP-BP/lnpbps/pulls/__>
Status: Proposal
Type: Standards Track
Created: 2021-06-19
Finalized: not yet
License: CC0-1.0
```

## Abstract

## Background

## Motivation

## Design

Strict encoding is designed with the following goals:
* portability, or platform-independence: it must be compatible with different 
  computing architectures, instruction set architectures and in networking 
  systems without modification;
* determinism: any two strict encoded data which differ in their byte sequence 
  will represent semantically-distinct information pieces;
* resource limits: any strict-encoded data can be accessed and computed on a 
  limited-resource systems (embedded systems), since none of atomic encoding 
  data pieces can exceed 64kb in size;
* extensibility: strict encoding typing may be extended with new types using 
  provided notation system; these extensions include TLV extensions used for 
  agile networking RPC contracts (like in Lightning network-based protocols, for 
  instance Bifrost).

## Specification

### Formal semantics

**Data types**:
- Byte value
- Fixed-size typed array
- Variable-size typed array
- Composite type
- Typed optional

**Composition**:


### Notation syntax

Strict encoding notation consists of type composition. Each type is defined
within parentheses which 

type = type_alias | type_def
type_alias = `(` ident type `)`
type_def = data_type*
data_type = byte | fixed | array | optional
byte = `byte`
fixed = data_type `[` length `]`
array = data_type `[]`
optional data_type `?`

Examples:
```
(hash256 (byte:32))
(hash160 (byte:20))
(xcoord_pubkey (byte:32))
(uncompressed_pubkey (04 (x byte:32) (y byte:32)))
(even_pubkey (02 xcoord_pubkey))
(odd_pubkey (03 xcoord_pubkey))
(tx (version inputs outpus lock_time))
(version byte)
(inputs input[])
(input ((prev_outpoint outpoint) (sig_script byte[]) (witness (byte[])[])? (nseq byte))
```


## Compatibility

**Bitcoin consensus encoding**

**Lightning network encoding**

**Protocol buffers**

**CBOR**


## Rationale

## Implementations

## Acknowledgements

## References

## Copyright

This document is licensed under the Creative Commons CC0 1.0 Universal license.

## Test vectors
