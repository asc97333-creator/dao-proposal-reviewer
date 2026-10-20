# Studio verification — 2026-10-20

Network: GenLayer Studio sandbox. Execution mode: Normal (Full Consensus), simulation mode off. No external personal wallet was connected.

Contract: https://explorer-studio.genlayer.com/address/0x5314396ddA84b8E55416dA76F46E96a554cE8B9e
Organizer: 0xc1E2D10a6716b921D106c13AA31e7E02F651429c
Unauthorized test account: 0x631A76a2a757B2E9cCe8D69f96f1178FFcdb2ea8

## Transactions

| Action | Hash | Verified result |
|---|---|---|
| Deploy | 0x629231f27792c226d886e9761e2715bb28725eeda190d0f64f0a75770f40c249 | FINALIZED; SUCCESS; consensus Accepted |
| Submit proposal | 0x9b51cd10579c3f62ea9df80d51ad6697023d763cf36ce0c009c7ed2ddad131b8 | FINALIZED; SUCCESS; proposal 1 stored |
| Initial comparative analysis | 0x2e60d2c4082ada385aa070ed7e0b3f759982236e405fd2af96cbd826fe789fb5 | FINALIZED lifecycle, but consensus Undetermined; analysis NOT committed. Not a successful analysis. |
| Same-code upgrade | 0xe4ed131dd33ff1875ea64699ead22f965ebede5177da6e71e4901d8ade6d57fa | FINALIZED; no functional change intended |
| Upgrade to source-grounded non-comparative validation | 0x7ca5827c2c2c1a46e3d8d0c5f4d74fc930255cb1747380cd245a7ff564acc81e | FINALIZED |
| Revised AI analysis | 0x48db0c6b2debbbb5dbe7179e89485d395ba66ac6fdaf7819a8fb00bc91aa5249 | FINALIZED; SUCCESS; consensus Accepted; advisory review stored |
| Unauthorized decision | 0x3fe9bb9e147ffe0c45de84907319ee5f832038f99827ae89a131a55caec7880d | FINALIZED; ERROR; Rollback; Only organizer may record a decision. Expected rejection. |
| Organizer decision | 0xcfa07c4554c3d1d978094eafec5a22c9ea296e68dbd06257f5c5f4b2708f775b | FINALIZED in Studio; subsequent state read: FINALIZED, decision NEEDS_REVISION |

Transaction detail URLs use https://explorer-studio.genlayer.com/tx/ followed by the exact hash above.

## State checks

- Initial get_proposal_count(): 0.
- get_organizer(): matches deploying organizer above.
- After submission: proposal 1 title Improve DAO Contributor Grants, organizer as submitter, status SUBMITTED.
- After revised analysis: ANALYZED_AWAITING_DAO_DECISION; summary, benefit, risk and missing information populated.
- After organizer decision: status FINALIZED; decision NEEDS_REVISION; analysis preserved.

## Limits and outstanding work

- Website remains an offline demonstration. GitHub Pages publication pending browser authentication.
- GenLayer Projects mission has not been submitted or accepted.
- Nonexistent ID, invalid decision, repeated review and input boundary tests have not yet been run.
- Studio's FINALIZED lifecycle alone does not prove execution success; inspect GenVM and consensus results and read stored state.
- Advisory AI output is not a DAO vote and cannot execute proposals or move tokens.
