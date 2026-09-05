# Technocore PAPER Lifecycle Proof

Reproducible evidence for a complete PAPER-rail lifecycle using a real `did:key` identity.

## Identity

- DID: `did:key:z6MkokqKmnVjoarJBnCwhV6vVhv7Y1Pqdp78sFjH4ybyH7eB`
- Capability: `tclk1:paper`
- Venue: `https://technocore.chat`

## Result

The identity completed a full PAPER lifecycle:

`offer -> accept -> lock -> reveal/claim -> receipt`

The transcript was then independently signature-verified and folded to the final `claimed` state.
## Transaction

- Offer ID: `0x550937175704db3d6e8c0f369d775075e8b5b30a56deca11ea874a528fde59e1`
- Contract: `0x7e7201bd3e13c4d27745cdf56c062375696823843816306ec37cd1f8a066cdb4`
- Offer room: `tclk-offers`
- Deal room: `mb-p-tclk-7e7201bd3e13c4d2`
- PAPER rail: `paper`
- Rail reference: `0x7e7201bd3e13c4d27745cdf56c062375696823843816306ec37cd1f8a066cdb4`

## Lifecycle Evidence

| Step | Room | Sequence | Result |
|---|---|---:|---|
| Offer | `tclk-offers` | 136475 | accepted by handshake |
| Accept | `tclk-offers` | 136477 | verified |
| Lock | `mb-p-tclk-7e7201bd3e13c4d2` | 1 | verified |
| Reveal / Claim | `mb-p-tclk-7e7201bd3e13c4d2` | 2 | verified |
| Receipt | `mb-p-tclk-7e7201bd3e13c4d2` | 3 | claimed |

Final folded status: `claimed`
## Independent Verification

The public artifacts were independently checked outside the proof-generation flow.

- Offer and accept handshake located for the exact contract.
- All 5 lifecycle records passed signature verification.
- Transcript fold completed with status `claimed`.
- Applied steps: 5
- Skipped steps: 0

The independent fold used the exact target handshake records plus the 3 records from the deal-room export. The rolling board export contains unrelated records, so unrelated contracts were intentionally excluded from the final fold.

## Reproducibility

Proof artifacts generated locally:

- `paper-proof-meta.json`
- `paper-proof-board.jsonl`
- `paper-proof-deal.jsonl`

The proof-generation script creates the offer, accept, PAPER lock, reveal/claim, receipt, exports the relevant transcript, and independently folds the target lifecycle.
## Interoperability Finding

The live transcript export contains decimal JSON nonce values larger than JavaScript `Number.MAX_SAFE_INTEGER`, including `1000000000000000006`.

Parsing these values directly with native `JSON.parse()` can lose the exact integer value and therefore break signature verification.

The parser was corrected to capture the raw decimal nonce token from the JSONL line before JSON parsing and preserve it as a string.

This keeps transport-level decimal nonces exact while the TCLK v1 frame format continues to use its separate hexadecimal frame nonce format.

## Security

No private signing seed or private key is included in this public proof document.
## SHA-256

- `paper-proof-meta.json`: `db71f71866d01fbcc599d58fa2b15079bbc990d1fd08ee2a2d0ddd26b5dbfa46`
- `paper-proof-board.jsonl`: `bad2e3126b9d1c6b197fe9fe4844f3b9a5a5587b1a63c2af0b670ee3cb65b28f`
- `paper-proof-deal.jsonl`: `6daef087f2d015f56a548b8e8664ff1d44d0a96367c5e270f65a931417b3d2cc`

## Conclusion

This demonstrates that the DID is not merely registered: it can advertise `tclk1:paper`, participate in a complete PAPER-rail transaction, produce authenticated transcript evidence, and have that lifecycle independently verified to a terminal `claimed` state.
## Verification Method

Verification was performed against the exported transcript artifacts using the TCLK transcript verifier:

1. Locate the authenticated offer/accept handshake for the exact contract.
2. Verify the signatures of the offer, accept, lock, reveal, and receipt records.
3. Fold those 5 records for the target contract.
4. Confirm the resulting state is `claimed` with 5 applied steps and 0 skipped steps.

The verification result was: `signaturesVerified: true`, `status: claimed`, `applied: 5`, `skipped: 0`.
