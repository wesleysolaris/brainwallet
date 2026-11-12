# Brainwallet

**One secret phrase → Bitcoin and Nostr keys.**

**Brainwallet** is a free, open-source (MIT-licensed), experimental HTML/JavaScript prototype that deterministically derives Bitcoin and Nostr cryptographic keys from a user-provided secret phrase.

> [!WARNING]
> **Do not use Brainwallet to store real Bitcoin funds.** This project has **not been security audited** and is not a production-ready wallet. Human-chosen phrases may be predictable and vulnerable to dictionary or brute-force attacks. Never share your secret phrase, private keys, or recovery words—including in bug reports.

## Concept

Traditional Bitcoin wallets typically generate a random recovery phrase that the user must keep safe. Brainwallet explores the reverse approach: **the user chooses a secret phrase, and the application calculates the corresponding keys**.

With identical input, algorithm versions, and parameters, the same keys can be reconstructed. **This does not make a memorized phrase as secure as a cryptographically random recovery phrase.**

## How it works

```text
              User-chosen secret phrase
                         |
                      Argon2id
                         |
               Derived key material
                         |
             +-----------+-----------+
             |                       |
          Bitcoin                   Nostr
      Addresses + WIF           npub + nsec
             |
        Optional BIP39
    Derived 12 or 24 words
       (separate wallet)
```

**Argon2id** increases the computational cost of guessing a secret, but **cannot make a weak phrase safe**. The optional BIP39 mnemonic is derived from the same underlying secret and represents a wallet distinct from the directly derived Bitcoin keys and the Nostr identity. **The mnemonic words are not independently random.**

## Features

- **Bitcoin:** Legacy and native SegWit addresses, plus a WIF private key.
- **Nostr:** public identity (`npub`) and private key (`nsec`).
- **Optional BIP39:** deterministic 12- or 24-word mnemonics for a separate wallet derivation.
- **Interface:** 20 language options, light/dark themes, expandable sections, and masked private values.
- **Open source:** source code available for study, inspection, modification, and contributions.

## Project principles

1. **Simplicity:** a minimal interface for exploring Bitcoin and Nostr key derivation.
2. **Autonomy:** help users understand how their input relates to the resulting cryptographic keys.
3. **Transparency:** make implementation details available for independent inspection and collaboration.

## Getting started

1. Select **Code → Download ZIP** on this repository.
2. Extract the ZIP archive.
3. Open `index.html` in Google Chrome or another modern browser.

The current version requires an internet connection to load some external cryptographic libraries and the English BIP39 word list. **It is not fully offline.** Key processing is performed in the browser, but this alone **does not guarantee privacy or security**.

## Security considerations and limitations

- **Experimental and unaudited:** do not use with real funds.
- **Human-chosen secrets are not cryptographic randomness:** the password-strength indicator is only a visual estimate, not a guarantee against attacks.
- **Deterministic compatibility:** changing algorithm versions or derivation parameters may produce different keys.
- **External dependencies:** remotely loaded libraries and word lists require security review and integrity protections before sensitive use.
- **Derived BIP39:** the recovery words depend on the original secret and are not equivalent to an independently generated random mnemonic.
- **Independent review required:** the cryptographic implementation, address compatibility, and handling of sensitive values need thorough testing and external audit.

Found a problem? Please open an **Issue** without including passwords, seed phrases, private keys, or financial details.

## License

Released under the **MIT License**. See [LICENSE](LICENSE).
