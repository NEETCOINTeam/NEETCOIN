## What is NEETCOIN?
**NEETCOIN is a PoS/PoW hybrid cryptocurrency.**

**NEETCOIN was created to support neet. "NEET" is an acronym "Not in Education, Employment or Training" and refers to those who are not involved in school, occupation, or vocational training.**

## SPEC
- Proof-of-Work consensus algorithm: Scrypt
- Proof-of-Stake annual interest: 21%
- Proof-of-Stake Super block: 210%
  - 10,000 ~ 12,100 blocks
  - 20,000 ~ 22,100 blocks
  - 40,000 ~ 42,100 blocks
  - 70,000 ~ 72,100 blocks
  - 100,000 ~ 102,100 blocks
  - After this, 2,100 super blocks every 50,000 blocks.
- Maxium Coin Supply: 2,100 Million
- RPC Port: 21010
- Port: 21011
- SegWit: Unimplemented
- Lightning Network: Unimplemented
- Atomic Swaps: Unimplemented

## Links
- **[NEETCOIN Website](https://neetcoin.jp/en/)**
- **[NEETCOIN Discord](https://discordapp.com/invite/wWG4AzV)**
- **[NEETCOIN Twitter](https://twitter.com/neetcoin_jp)**

## Build
- **[Unix Build](doc/build-unix.txt)**
- **[NEETCOIN-qt: Qt5 GUI for NEETCOIN](doc/readme-qt.rst)**

## How to run tests

```bash
mkdir build && cd build
cmake ..
make
./test_neetcoin --log_level=message
```
