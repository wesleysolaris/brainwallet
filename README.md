# Brainwallet

Experimental single-page HTML/JavaScript prototype for deterministic Bitcoin and Nostr key derivation using Argon2id.

> **Security warning:** This project has **not been audited**. Do not use it with real funds, private keys, or recovery phrases. User-chosen phrases may be guessable.

## Features

- Bitcoin Legacy, native SegWit, WIF
- Nostr npub and nsec
- Deterministically derived BIP39 12- or 24-word mnemonics (separate wallet derivation)
- 20 interface languages, light/dark themes, private-value masking

## Usage

Open `index.html` in Chrome or a modern browser. Internet access is needed to load external libraries and the BIP39 English word list. No server is needed. This is an experimental prototype, not a production wallet.

## Compatibility & security

Argon2id parameters must remain consistent to derive the same keys. The BIP39 mnemonic is **not independently random**; it is based on the input secret. The Bitcoin keys derived directly and the optional BIP39 wallet are different. Strength estimates are heuristics, not cryptographic guarantees. The code and dependencies need independent security review.

Please do not include real secrets in bug reports.

## License

MIT. See [LICENSE](LICENSE).
