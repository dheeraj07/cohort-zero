# Notes

This document is intended as a collection of ideas, thoughts and information.

## Stateless Ethereum

Enable validators to be able to validate blocks without requiring state. Instead 
use block witnesses to validate the resulting state root.

### Resources

- Starting point: 
    - https://hackmd.io/@vbuterin/state_size_management
    - https://blog.ethereum.org/2019/12/30/eth1x-files-state-of-stateless-ethereum/
    - https://ethresear.ch/t/an-updated-roadmap-for-stateless-ethereum/9046
    - https://dankradfeist.de/ethereum/2021/02/14/why-stateless.html
- Cryptography attack:
    - Elliptic curve pairings: https://vitalik.ca/general/2017/01/14/exploring_ecp.html
    - Kate polynomial commitments: https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html
    - Verkle tries: 
        - https://vitalik.ca/files/misc_files/verkle.pdf
        - https://notes.ethereum.org/_N1mutVERDKtqGIEYc-Flw
        - https://notes.ethereum.org/nrQqhVpQRi6acQckwm1Ryg
- Block access lists: https://ethresear.ch/t/block-access-list-v0-1/9505

### Keywords

- Verkle tries (reduce proof size, c.f. merkle proofs)
- Kate polynomial commitments (no idea yet)
- Dynamic vs static state access (can we predict from the transaction data alone, which state will be touched)
- (Block) witness (information needed for new state root)
- Block access lists (not clear yet, but related to question 3.)
- State expiry (untouched state becomes expired after some time, reactivation requires a proof, introducing state rent and possibly a max state size)
- Regenesis (move all current state in a new genesis block, possibly including state expiry)

### Thoughts and Questions

1. The idea behind a verkle trie is to (somehow) reduce the witness size, which is information needed to be able to verify a new state root.
2. The naive way to do this is a merkle proof (impractical, because too big in size).
3. How does the validator know, that the witness information is not manipulated?
