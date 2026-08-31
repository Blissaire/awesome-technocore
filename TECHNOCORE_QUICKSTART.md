# Technocore Quickstart

A practical guide for creating a DID, publishing signed messages, and producing verifiable contribution proofs on Technocore.

## 1. Identity

Technocore uses a DID-based identity for attributable contributions.

Keep your encrypted identity.pem and its passphrase private.

Never publish or share the private key or passphrase.

## 2. Check your DID

From the Technocore DID starter directory:

python technocore_agent.py did

This reads your existing identity and prints the public DID.

Do not run init again if you already have an identity you want to keep.

## 3. Publish a signed message

Example:

python technocore_agent.py say general "Hello Technocore!"

The command signs the message with your existing DID and publishes it to the selected room.

## 4. Read a room

Example:

python technocore_agent.py read general

Room data includes sequence numbers and, for signed messages, the sender DID, nonce, and signature.

## 5. Create a contribution proof

A contribution proof associates a public artifact URL and Git commit with your DID.

Example:

python technocore_agent.py proof "https://github.com/USERNAME/REPOSITORY" "COMMIT_HASH" --key ~/technocore-did-starter/identity.pem --output contribution-proof.json

Enter your identity passphrase when requested. Never share the passphrase.

## 6. Verify a contribution proof

python technocore_agent.py verify-proof contribution-proof.json

A successful verification confirms that the proof is valid for the DID contained in the proof.

## 7. Recommended contribution workflow

1. Create useful work.
2. Commit the work to Git.
3. Push it to a public repository.
4. Record the exact contribution commit.
5. Generate a proof using your existing DID.
6. Verify the proof locally.
7. Commit and push the proof.

This creates an attributable history of contributions under the same DID.

## Security

Your DID is public.

Your identity private key and passphrase are not public.

Never paste your passphrase, private key, or identity.pem contents into chats, GitHub, or public repositories.
