# Security policy

Report vulnerabilities privately to `contact@ali-hasanov.com`. Do not open a public issue for authentication bypasses, credentials, private conversation content, or prompt-injection paths with sensitive impact.

## Security requirements

- Keep Anthropic, database, JWT, and Twilio credentials in environment variables.
- Apply authentication and role checks to every administrative route.
- Treat user messages and retrieved documents as untrusted input.
- Do not allow retrieved content to change system policy or tool permissions.
- Minimize stored conversation content and redact secrets and sensitive identifiers from logs.
- Verify Twilio signatures before trusting inbound webhook requests.
- Rate-limit public chat and authentication endpoints.

## AI-specific risks

The assistant must not invent policy, expose hidden instructions, or represent uncertain content as authoritative. When grounding is insufficient, it should ask a clarifying question, provide a bounded response, or escalate to a human operator.

Only the latest revision is supported.
