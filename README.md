# ChromaCode

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
