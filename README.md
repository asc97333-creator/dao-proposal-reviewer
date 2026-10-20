# AI DAO Proposal Reviewer

A distinct GenLayer Intelligent Contract prototype for *advisory AI analysis of DAO proposals with an organizer-controlled final decision*. This is not QuestProof and does not attempt to verify GitHub evidence or distribute rewards.

## Current status

- **Deployed and tested in the GenLayer Studio sandbox** on 2026-10-20. Deployment, proposal submission, revised AI analysis and organizer decision reached FINALIZED; stored proposal state was verified.
- Unauthorized decision attempt rolled back with the expected organizer-only error. Initial AI analysis failed consensus; this is recorded explicitly.
- See [verification evidence](docs/VERIFICATION.md) for exact hashes and outstanding tests. GitHub Pages publication and mission submission are still pending.
- Site (`index.html`) is an **interactive off-chain illustration**, not a connected contract client.

## Contract workflow

1. Any wallet submits a substantive DAO proposal with `submit_proposal(title, description)`.
2. Anyone triggers `analyze_proposal(proposal_id)` using GenLayer's source-grounded non-comparative Equivalence Principle. The result is *advisory*, not a vote.
3. Only the deploying organizer wallet calls `record_decision(proposal_id, decision)` with `APPROVED`, `REJECTED`, or `NEEDS_REVISION`.
4. All users inspect the record using `get_proposal(proposal_id)` and count using `get_proposal_count()`.

## Security / product scope

- The LLM reviews **submitter-controlled proposal text**, not external evidence. No claims of identity, proposal authorship, execution, or community vote authentication.
- The organizer is the sole authorized decision recorder, not a multi-member on-chain DAO ballot. The final recorded decision should be treated as an **organizer attestation**.
- The AI's advisory output can be inaccurate. Independently review the submission and analysis.
- The frontend is a local demo, and will not read or write on-chain state until separately integrated.

## GenLayer Studio tests to perform

1. Deploy from organizer wallet; verify `get_organizer()` and count `0`.
2. From participant wallet, submit proposal title `Improve DAO Contributor Grants` and detailed proposal body (40+ chars). Check returned proposal ID.
3. `get_proposal(id)` must show `SUBMITTED` and sender address.
4. Run `analyze_proposal(id)`. Confirm transaction finalizes, then `get_proposal(id)` should show `ANALYZED_AWAITING_DAO_DECISION` and advisory analysis.
5. From participant wallet, call `record_decision(id, 'APPROVED')` and confirm failure.
6. From organizer wallet, call `record_decision(id, 'NEEDS_REVISION')` and confirm `FINALIZED` and decision saved.
7. Test nonexistent ID, invalid decision and repeated review to confirm appropriate errors.

Completed checks and unrun cases are listed separately in docs/VERIFICATION.md. This is Studio sandbox evidence, not mainnet evidence.

## Official references

- [Your First Intelligent Contract](https://docs.genlayer.com/developers/intelligent-contracts/first-intelligent-contract)
- [Equivalence Principle](https://docs.genlayer.com/developers/intelligent-contracts/equivalence-principle)
- [GenLayer storage](https://docs.genlayer.com/developers/intelligent-contracts/storage)
