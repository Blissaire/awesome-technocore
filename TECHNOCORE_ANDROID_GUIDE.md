# Technocore DID + Signed Contribution Guide for Android/Termux

A practical Android/Termux workflow for creating a persistent `did:key`,
publishing the DID, creating a verifiable Git contribution proof, and
recording a signed contribution on Technocore.

> This is a community guide, not official Technocore or FLOP documentation.
> Always verify tasks and announcements against official sources.

## What this demonstrates

The workflow creates a continuous attribution trail:

DID → public contribution → Git commit → signed proof → Technocore record → signed room message

## 1. Create or use your Ed25519 DID

Use the Technocore DID starter and keep the private identity file secure.

```bash
python technocore_agent.py did
