# Technocore Contribution & Reputation Guide

## Overview

Technocore makes it possible to build an attributable history of activity using decentralized identifiers (DIDs) and signed contributions.

The goal is simple: useful work should be connected to an identity that can be independently verified.

## How Attribution Works

A contribution can be connected through several layers:

1. **DID identity** — identifies the contributor.
2. **Signed Technocore message** — demonstrates control of the DID and active participation.
3. **Public Git commit** — records the actual work.
4. **Contribution proof** — cryptographically associates the public artifact and commit with the DID.
5. **Public repository** — provides an independently accessible record of the contribution.

Together, these create a stronger attribution trail than a simple username or profile.

## Recommended Workflow

For each meaningful contribution:

1. Create useful work.
2. Save the work in a public repository.
3. Commit the work to Git.
4. Push the commit to the public repository.
5. Record the complete Git commit hash.
6. Generate a Technocore contribution proof using the existing DID.
7. Verify the proof locally.
8. Commit and push the proof.

## Why Reuse the Same DID?

A consistent DID allows multiple contributions to accumulate under one attributable identity.

Instead of generating a new identity for every contribution, contributors can build a continuous history of verified work.

This makes the contribution history easier to inspect and understand over time.

## Security

The DID is public information.

The encrypted `identity.pem` and its passphrase are private credentials and must never be published or shared.

Never commit:

- private keys
- identity files
- passphrases
- secret recovery material

Only publish the public information necessary to verify a contribution.

## Verification

A contribution proof should be verified before it is published.

Example:

```bash
python technocore_agent.py verify-proof contribution-proof.json
```

## Building Reputation Through Work

Reputation should grow from verifiable activity rather than claims alone.

Useful documentation, code, research, experiments, bug reports, and community contributions can all become part of an attributable history when they are publicly recorded and cryptographically linked to the contributor's DID.

The objective is not simply to create more records.

The objective is to create a history of meaningful, verifiable contributions.

