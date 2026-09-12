# Documentation Project Instructions

## About This Project

- This is the official developer documentation for **Wirebox** built on [Mintlify](https://mintlify.com).
- **Deployment Remote**: `git@github.com:wirebox-sh/docs.git` (`wirebox-sh/docs`). Pushing to `main` here automatically triggers Mintlify deployments to [https://docs.wirebox.sh](https://docs.wirebox.sh).
- **Sibling Codebase Repo**: The main product codebase (Next.js frontend, Hono edge worker API, and internal specs) lives in `../WireBox` (`wirebox-sh/wirebox`). Do not put internal system implementation specs here.
- Pages are MDX files with YAML frontmatter.
- Site navigation and configuration live in `docs.json`.
- All public API specifications live in `api-reference/` and mirror the public `/api/v1/*` contracts.

---

## CRITICAL RULE: User-Centric Perspective Only

> **DO NOT EXPOSE INTERNAL IMPLEMENTATION DETAILS. WRITE STRICTLY FROM THE USER'S PERSPECTIVE. IF THE USER DOES NOT NEED TO KNOW IT TO USE WIREBOX, DO NOT WRITE IT.**

1. **Zero Internal Implementation Jargon**:
   - **Never** mention internal cloud vendors, storage buckets, database technologies, or internal parsing libraries (e.g., Cloudflare Workers, Cloudflare R2, Cloudflare D1, Supabase, PostgreSQL, PostalMime, etc.).
   - **Never** expose internal system architecture diagrams, database schemas, internal queue mechanics, or private infrastructure lifecycle diagrams.
2. **Focus Exclusively on Developer / User Value**:
   - Focus on what the developer or autonomous agent can achieve with the API.
   - Document how to authenticate, how to make requests, parameters, response formats, headers, and error codes.
   - Explain features by their capabilities and behavior (e.g., "Attachments are stored securely and served via signed download URLs", NOT "Attachments are streamed to R2 buckets via PostalMime").
3. **The "Need-to-Know" Filter**:
   - Before writing any paragraph or sentence, ask: *"Does an external developer or agent need to know this to integrate with Wirebox?"*
   - If the answer is no, **omit it completely**.

---

## Terminology

- **Identity**: A real-world agent identity container (`id: ident_...`). Can have multiple communication channels (email, phone, etc.).
- **Mailbox**: An email address provisioned for an identity (`agent@wirebox.sh` or custom domain).
- **Thread**: An RFC-5322 email conversation grouping related messages.
- **Message**: An individual inbound or outbound email (`msg_...`).
- **Webhook**: Real-time event notifications delivered via HTTP POST with cryptographic signatures.
- **API Key**: Bearer authentication token for programmatic API access (`wb_live_...`).

---

## Style Preferences

- **Tone**: Clear, professional, developer-first, and concise.
- **Perspective**: Second person ("you") and active voice.
- **Conciseness**: Keep sentences short and direct — one idea per sentence.
- **Formatting**:
  - Sentence case for titles and headings.
  - Bold for UI elements: Click **Create Identity**.
  - Inline code for parameter names, endpoints, file names, and headers: `GET /api/v1/mailboxes`, `wb_live_...`, `Authorization`.
  - Provide full, executable code snippets in cURL, Python, and TypeScript.

---

## Content Boundaries

### What to Document
- Getting started, quickstart guides, and onboarding flows.
- Public REST API endpoints (`/api/v1/*`) with request/response examples.
- Webhook events, payload schemas, and signature verification.
- Developer workflows (sending emails, receiving webhooks, managing threads).
- Security, rate limits, and error handling from the consumer's viewpoint.

### What NOT to Document
- Internal infrastructure, hosting providers, or vendor names (Cloudflare, Supabase, etc.).
- Internal system architecture diagrams or internal data pipeline diagrams.
- Private backend implementation details, internal helper libraries, or database tables.
- Roadmap promises or unreleased internal features without public endpoints.
