# Université libre de Bruxelles (ulb)

Université libre de Bruxelles (ULB) is a major French-speaking research university in Brussels, Belgium, ranked #230 in the QS World University Rankings 2025. Its publicly documented developer footprint centers on DI-fusion, the university's institutional research repository, which exposes a documented HTTP export API, a search interface, RSS feeds, and an OAI-PMH harvesting service. ULB also maintains an official GitHub organization for departmental and research code.

- APIs.json: https://raw.githubusercontent.com/api-evangelist/ulb/refs/heads/main/apis.yml
- Run with Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=ulb-api-evangelist&utm_content=repo

## Type

- Index
- Consumer
- 3rd-Party

## Tags

Education, Higher Education, University, Research, Open Access, Institutional Repository, Belgium

## APIs

- **DI-fusion Scholar Export API** — exports a given scholar's publication list (APA, BibTeX, RIS, CSV, xml-brief/-ext/-full) from `difusion-svc.ulb.ac.be/scholar`. Docs: https://bib.ulb.be/en/find-documents/di-fusion
- **DI-fusion Group Export API** — exports publication lists for a group of scholars from `difusion-svc.ulb.ac.be/group`. Docs: https://bib.ulb.be/en/find-documents/di-fusion
- **DI-fusion OAI-PMH Harvesting Service** — documented OAI-PMH metadata harvesting for the institutional repository. Docs: https://bib.ulb.be/en/find-documents/di-fusion/terms-of-use

## Plans

- [plans/ulb-plans-pricing.yml](plans/ulb-plans-pricing.yml)

## Rate Limits

- [rate-limits/ulb-rate-limits.yml](rate-limits/ulb-rate-limits.yml)

## FinOps

- [finops/ulb-finops.yml](finops/ulb-finops.yml)

## Timestamps

- Created: 2026-06-03
- Modified: 2026-06-03

## Common Properties

- Website: https://www.ulb.be/en
- GitHub: https://github.com/ulb
- LinkedIn: https://be.linkedin.com/school/universite-libre-de-bruxelles/
- Source Code: https://github.com/ulb

## Notes

The DI-fusion Scholar export API was verified live (HTTP 200, valid XML). The DI-fusion Download & API technical PDF documents the Scholar, Group, search, RSS, sitemap and OAI-PMH services. The VuFind OAI-PMH paths probed returned HTTP 500, so the OAI service is cataloged from documentation rather than a verified live response. No public student/SIS, timetable, library discovery, or SSO API documentation was found. No endpoints were fabricated.

## Maintainers

- Kin Lane — kin@apievangelist.com
