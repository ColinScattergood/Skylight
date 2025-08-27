# Unofficial Skylight API (Community Reference)

> **Purpose**: A community-maintained reference for documenting the network endpoints used by the Skylight apps, based on observed traffic.  
> **Scope**: Reverse-engineered, incomplete, and **unofficial**. Not affiliated with Skylight. For research, interoperability, and educational use only.

---

## Disclaimers

- Respect the app’s Terms of Service and privacy laws. Only capture traffic from your own account/devices.
- Redact personal data and secrets (tokens, emails, IDs tied to real people) before committing.
- This repository **does not** encourage abusing the service or bypassing protections.

## Repo Organization

- `openapi/openapi.yaml` — OpenAPI 3.1 spec for discovered endpoints.
- `examples/` — Example requests/responses (redacted).
- `docs/` — How-to guides (auth, capturing traffic, etc.).
- `CONTRIBUTING.md` — How to add endpoints/schemas.
- `SECURITY.md` — Responsible redaction guidelines.
- `LICENSE` — Default: CC BY-NC 4.0.

## Base URL

```
https://app.ourskylight.com
```

Most endpoints live under `/api/...` and follow **JSON:API** (`type`, `id`, `attributes`, `relationships`).

## Authentication

Skylight’s mobile app uses a Bearer token:

```
Authorization: Bearer <REDACTED>
```

Tokens rotate. Treat them as secrets. See [docs/auth.md](docs/auth.md) for guidance.

## Example Endpoint

- `GET /api/frames/{frameId}/chores` — List chores for a frame within date bounds.  
  See the OpenAPI spec for full parameters and response.

## Tools & Workflow

- **Capture**: Charles / Proxyman / mitmproxy.
- **Inspect**: Confirm hostnames and query params.
- **Document**: Update `openapi/openapi.yaml` with new schemas/endpoints.
- **Test**: Postman/Insomnia against your own account.

## Roadmap

- Add auth/login flow (if observable).
- Expand coverage: chores create/update, categories, profiles, frames, rewards, schedules.
- Document rate limits, error shapes, pagination.

---

## Interactive Docs

You can explore the API spec in your browser:

- [Swagger UI](docs/swagger.html) — interactive “try it” interface  
- [Redoc](docs/redoc.html) — clean reference-style docs

On GitHub Pages these will be published at:

- `https://<user>.github.io/<repo>/docs/swagger.html`  
- `https://<user>.github.io/<repo>/docs/redoc.html`

---

## Local Preview

```bash
# from repo root
python3 -m http.server 8080
# then browse http://localhost:8080/docs/swagger.html
```

---

### Versions

- **v0.2.0** — Categories, Devices, Lists, Task Box endpoints; Basic auth scheme.  
- **v0.3.0** — Frames, Source Calendars, Calendar Events, Rewards, Reward Points; expanded schemas; corrected color formats; explicit `chore.status`.

---

Maintainers: add yourself to [docs/maintainers.md](docs/maintainers.md) if you contribute regularly.
