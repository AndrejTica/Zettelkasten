---
date: 2025-10-28
tags:
  - "#crypto" 
---
## Kerckhoffs principle
The algorithm should not be a secret, only the key.

## Types of cryptographic attacks

- COA (Ciphertext-only attack).
The attack is done using only the cipher text and nothing else. 

- KPA (Known-plaintext-attack).
The attacker knows a part of the plain text. For example if they know the
document type, like a PDF, which has a known magic number, they know a part of
the cipher text.

- CPA (chosen-plaintext-attack).
The attacker can choose a plaintext and has the possibility to get the
corresponding ciphertext. This attack can be done when the attacker has the
access to the machine that encrypts.

- CCA (Chosen-ciphertext).
The attacker can choose a cipher text and can decrypt it to get the
corresponding plain text.

The last two types of attack are active and not passive, which means the
attacker has to use some ticks can gain access to information or tools they
don't have by default.

In cryptography, we want the cipher text to give no information about the plain
text, only its length. This is called semantic security. 

The attacker, given two texts, should also not be able to tell which one of the
two texts was encrypted. This is called Ciphertext indistinguishability (IND).
Imagine it like this if we have two messages that were encrypted:
So if someone sees the ciphertext, they should not be able to say:

“this ciphertext is probably message A”
“this one is probably message B”

better than a coin flip. If its better than a coin flip then IND is achieved. 

## IND-CPA
This means the attacker is allowed to choose plaintexts themselves and ask:

“Encrypt this”
“Encrypt that”
“Encrypt this too”

So the attacker is not passive. They can experiment with the encryption system.
IND-CPA safety is a basic requirement for cypto systems.

## Non-Malleability
Non-malleability means:

An attacker should not be able to take a ciphertext and change it in a 
meaningful way so that the decrypted message becomes a related message.


