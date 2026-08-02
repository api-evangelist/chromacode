# ChromaCode

ChromaCode, Inc. is a Carlsbad, California molecular diagnostics company. Its High-Definition PCR (HDPCR) chemistry multiplexes more than four times the targets of conventional digital PCR on existing qPCR and dPCR instruments, and ChromaCode Cloud decodes the raw run files into interpreted variant calls and downloadable reports. Products span oncology tumor profiling (the HDPCR NSCLC panel), minimal residual disease and disease monitoring, and transplant rejection.

- Website: https://www.chromacode.com/
- ChromaCode Cloud: https://www.chromacode.com/chromacode-cloud/ (application: https://chromacodecloud.com/)
- GitHub: https://github.com/ChromaCodeINC
- Secondary-market listing: https://forgeglobal.com/chromacode_stock/

## API posture

ChromaCode publishes **no public API**. There is no developer portal, no OpenAPI/Swagger/GraphQL/AsyncAPI definition, no SDKs on any package registry, no MCP server, and no A2A agent card.

The ChromaCode Cloud product does run a REST API at `https://chromacodecloud.com/api`, but it is gated: every path returns HTTP 401 anonymously, and access is brokered by a Keycloak OpenID Connect identity provider at `openid.chromacodecloud.com`. That identity provider's discovery documents *are* publicly readable, so this repo captures a real, verifiable authentication and scope profile even though no API contract is published.

## Artifacts

| Artifact | What it holds |
|---|---|
| `apis.yml` | APIs.json 0.20 index — identity, the gated ChromaCode Cloud API entry, and every artifact pointer |
| `well-known/` | Probe index for every host/path (with statuses) plus the two verbatim Keycloak OIDC discovery documents |
| `authentication/` | OIDC/OAuth 2.0 profile — flows, endpoints, PKCE, PAR, CIBA, device grant, mTLS-bound tokens |
| `scopes/` | The `scopes_supported` of both realms, including `chromacloud` and `chromacloud:service_account` |
| `conventions/` | Observed auth style, error envelope, CORS, transport, and the resource paths the front end calls |
| `errors/` | The observed 401 authorization envelope, and a 500 error-handling defect on unmatched `/api` paths |
| `lifecycle/` | Product version 6.1.0, RUO regulatory mode, milestones; no status page, SLA, or deprecation policy |
| `conformance/` | Verified OAuth/OIDC conformance plus ChromaCode's vendor-asserted HIPAA / HITRUST / ISO 13485 / GDPR claims |
| `security/` | TLS, HSTS, DNSSEC, CAA, SPF and DMARC posture for both domains |
| `llms/` | Agent-readable summary of the company and this repo |
