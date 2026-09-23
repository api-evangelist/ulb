# Université libre de Bruxelles (ulb)

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

Université libre de Bruxelles (ULB) is a French-speaking research university in Brussels, Belgium, founded in 1834 and funded through the Fédération Wallonie-Bruxelles. Unusually for a university, ULB operates its research infrastructure itself rather than renting it: there is no Figshare, Elsevier Pure, Dataverse or Ex Libris Esploro tenant under ULB's name, and the one documented API it publishes is its own engineering. Every surface profiled here is `x-operator: institution`; none is a vendor's contract running under the university's name.

- APIs.json: https://raw.githubusercontent.com/api-evangelist/ulb/refs/heads/main/apis.yml
- Run with Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=ulb-api-evangelist&utm_content=repo

## Type

- university — Public Research University
- Index
- Provider
- Public

## Tags

University, Higher Education, Education, Belgium, Europe, Research, Research Data, Institutional Repository, Open Access, Identity Federation, OAI-PMH, Library

## APIs

All four surfaces are operated by ULB itself, on ULB's own registrable domains (`ulb.be`, `ulb.ac.be`).

- **DI-fusion Export API** — `https://difusion-svc.ulb.ac.be` — bespoke ULB service exporting a scholar's or group's publication list in APA, BibTeX, RIS, CSV and three ULB XML formats. No credential required. Documented by the ULB Libraries in a 15-page PDF. Verified live 2026-08-30. [OpenAPI](openapi/ulb-difusion-export-openapi.yml)
- **DI-fusion OAI-PMH Harvesting Endpoint** — `https://difusion.ulb.ac.be/vufind/OAI/Server` — answers `Identify` and `ListMetadataFormats` with valid OAI-PMH 2.0 documents, but rejects the `oai_dc` prefix it advertises on every record-bearing verb. Present, registered, and not harvestable. [OpenAPI](openapi/ulb-difusion-oai-pmh-openapi.yml)
- **DI-fusion OpenSearch Description** — `https://difusion.ulb.ac.be/vufind/Search/OpenSearch` — OpenSearch 1.1 description for the self-hosted VuFind discovery layer. HTTP 200.
- **ULB Shibboleth Identity Provider (SAML 2.0 metadata)** — `https://auth.ulb.be/idp/metadata` — complete, unauthenticated SAML 2.0 metadata for entityID `https://auth.ulb.be/idp`, registered in the Belnet R&E Federation and published to eduGAIN. Carries the REFEDS Research & Scholarship entity category and SIRTFI assurance certification. The most complete contract ULB publishes.

## What was measured, and what is broken

Probed 2026-08-30. Every row is a status code, not a link.

| Surface | Result |
|---|---|
| `GET /scholar` (xml-brief, apa/pdf, bibtex, ris, csv) | 200, live bibliographic data |
| `reftype=xml-full` | **403** — the richest documented format, five pages of ULB's own PDF, is not publicly reachable |
| `reftype=xml-brief-ext` | **500** — the format added by the 03/2023 documentation revision |
| missing mandatory param, unknown `scholarID` | **500** Tomcat page, never a 4xx |
| OAI-PMH `verb=Identify` | valid protocol document under **HTTP 500**, with `Unknown Action` and a full HTML page appended after `</OAI-PMH>` |
| OAI-PMH `ListRecords&metadataPrefix=oai_dc` | 200 `badArgument: Missing Metadata Prefix` — **nothing is harvestable** |
| OAI-PMH `<request>` echo | `http://digital.library.villanova.edu/OAIServer.php` — the unmodified VuFind demo default |
| unAPI server (advertised in the DI-fusion HTML head) | port 8080 does not answer |
| `dipot.ulb.ac.be` (DSpace, serves the full-text links) | **500** "DSpace at ULB: Internal system error" |
| `gehol.ulb.be` (timetable), `cible.ulb.be` (discovery) | resolve in DNS, TCP times out — not assessable |
| `llms.txt`, `.well-known/security.txt` | 404 |

DI-fusion is registered as an OAI-PMH compliant repository in OpenDOAR, ROAR and Sherpa. A harvester that trusts that registration will collect nothing.

## Domain standards (Kin Score `education` regime)

Met: `saml`, `shibboleth`. Partial: `oai-pmh` (present, not harvestable). Documented but unverifiable: `orcid`. Absent, with no public evidence: `scim`, `lti`, `oneroster`, `ed-fi`, `caliper`, `qti`, `datacite`, `crossref`. Full evidence in [conformance/ulb-domain-standards.yml](conformance/ulb-domain-standards.yml).

## Artifacts

- [openapi/](openapi/) — two OpenAPI 3.1 descriptions (`derived`; ULB publishes none of its own), with pristine copies in [openapi/_original/](openapi/_original/)
- [json-schema/](json-schema/) — the xml-brief publication-list shape
- [examples/](examples/) — seven verbatim captured responses, each with request, status and byte count in [examples/index.yml](examples/index.yml)
- [vocabulary/](vocabulary/) — ULB's own `info:ulb-repo/semantics/` publication-type namespace plus the groupBy, roles, markup and reftype/filetype vocabularies
- [errors/](errors/) — eleven measured failure modes
- [rules/](rules/) — fifteen consumption rules, including the GDPR rule against enumerating matricules
- [authentication/](authentication/), [scopes/](scopes/), [conformance/](conformance/), [lifecycle/](lifecycle/)
- [plans/](plans/ulb-plans-pricing.yml), [rate-limits/](rate-limits/ulb-rate-limits.yml), [finops/](finops/ulb-finops.yml), [security/](security/ulb-domain-security.yml)

## Timestamps

- Created: 2026-06-03
- Modified: 2026-08-30

## Common Properties

- Website: https://www.ulb.be/en
- Portal (DI-fusion): https://difusion.ulb.ac.be/
- Research Repository: https://bib.ulb.be/en/find-documents/di-fusion
- Documentation (DI-fusion – Download & API, PDF): https://bib.ulb.be/medias/fichier/difusion-download-and-api_1678451163130-pdf?ID_FICHE=10054&INLINE=FALSE
- Identity Federation: https://auth.ulb.be/idp/metadata
- Library Catalog: https://bib.ulb.be/en
- Course Catalog: https://www.ulb.be/fr/se-former/catalogue-des-formations
- AI Policy: https://www.ulb.be/fr/intelligence-artificielle/note-dintention-relative-aux-outils-dia-dans-lenseignement-a-lulb
- AI Tooling (AcademIA): https://www.ulb.be/fr/intelligence-artificielle/academ-ia
- GitHub Organization: https://github.com/ulb
- Terms of Service: https://bib.ulb.be/en/find-documents/di-fusion/terms-of-use
- Privacy Policy: https://www.ulb.be/fr/mentions-legales/politique-de-protection-des-donnees-a-lulb
- Support: https://www.ulb.be/en/contact-us
- Blog: https://www.ulb.be/fr/actus-et-agenda
- LinkedIn: https://be.linkedin.com/school/universite-libre-de-bruxelles/
- ROR: https://ror.org/01r9htc13

## Notes

Re-profiled 2026-08-30 under the API Evangelist university pipeline, which settles operator attribution before saving anything. The previous profile held three `apis[]` entries with no `x-operator`, one of which carried no base URL at all and was invisible to the cohort audit. Nothing vendor-attributed was found to remove — ULB is one of the few institutions in this cohort with no vendor tenant. The scholar and group exports were consolidated into the single contract they belong to, and the OAI-PMH, OpenSearch and SAML surfaces were located, probed and given real base URLs. No public student/SIS, timetable, library discovery or open-data API was found; the timetable and discovery hosts exist but do not answer from the public internet. No endpoints were fabricated.

## Maintainers

- Kin Lane — kin@apievangelist.com
