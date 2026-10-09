---
name: logius-fsc-contract-lifecycle
description: Establish a connection between FSC Peers - announce, submit and accept a contract, then obtain an access token for a Service.
api: logius:fsc-core-manager
generated: '2026-10-09'
method: generated
source: openapi/logius-fsc-manager-openapi.yml
operations:
- announce
- getPeers
- getPeerInfo
- submitContract
- acceptContract
- rejectContract
- revokeContract
- getServices
- getToken
- getJSONWebKeySet
---
# FSC contract lifecycle (Logius FSC Core Manager)

FSC Core is a standard: every Peer runs its own Manager; there is no Logius-hosted base URL. Use the Manager of the Peer you are talking to.

1. `announce` (PUT /announce) — announce your Peer to the other Manager.
2. `getPeers` / `getPeerInfo` — discover known Peers and confirm who runs the Manager.
3. `submitContract` (POST /contracts) — submit a contract granting access to a Service.
4. The counterparty calls `acceptContract`, `rejectContract` (PUT /contracts/{hash}/accept|reject). Use `revokeContract` to withdraw a valid contract.
5. `getServices` — list Services for which a valid Contract exists.
6. `getToken` (POST /token) — obtain a JWT authorizing a connection to the Service.
7. `getJSONWebKeySet` (GET /.well-known/jwks.json) — fetch keys to verify signatures.

Rules: contracts are addressed by content hash; accept/reject/revoke are PUTs on a hash and are naturally repeatable. Error and auth details are defined in the FSC Core spec: https://logius-standaarden.github.io/fsc-core/
