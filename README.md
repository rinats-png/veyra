# Veyra

Veyra is a German-language invoicing workspace prototype. It provides a dashboard, customers, quotes, invoices, a rule-based natural-language draft assistant, print-to-PDF, local browser persistence, and JSON backup/import.

## Run locally

Serve `dist/` with any static HTTP server, e.g. `python3 -m http.server 8080 --directory dist` and open `http://localhost:8080`.

## Important limitations

- This is a browser-local functional prototype, not production billing software.
- Data lives in localStorage, with example records on first visit.
- The text assistant is a transparent regular-expression parser, **not an LLM**.
- PDF is a browser-print view; it is **not** an EN 16931, ZUGFeRD or XRechnung file.
- Do not send its documents as legally validated invoices without implementing and testing the compliance subsystem.
- No authentication, server database, mail, payment matching, Peppol or tax advice is supplied.

## Production roadmap

1. Replace localStorage with tenant-isolated PostgreSQL, server APIs, audit history and backups.
2. Add authentication, roles, MFA, rate limiting, consent and GDPR controls.
3. Integrate `gflohr/e-invoice-eu` for XML and hybrid PDF generation, with independent validation through Mustangproject/KoSIT test suites and version pinning. Validate all inputs and supported profiles.
4. Use an opt-in LLM solely to extract structured draft fields; calculate totals and taxes deterministically; provide field evidence and require human approval.
5. Add invoice lifecycle (number reservation, immutable issued snapshots, cancellation/credit notes), payment reconciliation, reminders, recurring invoices, email/Peppol transport and document retention workflows.
6. Security, legal and tax review before production use in Germany.

Third-party repositories are **not vendored** here. Their licenses and exact integration interfaces must be reviewed before inclusion.
