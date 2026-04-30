---
name: example-person-data
description: Provides consistent synthetic person records (names, contact, identifiers) for fixtures, demos, tests, and documentation without using real PII. Use when the user needs sample users, fake personas, seed data, anonymized examples, or placeholder people in code and docs.
---

# Example person data

## Principles

- Use **only fictional** names, emails, phone numbers, and addresses. Never copy real people or public figures.
- Prefer **deterministic** examples (same persona id → same fields) so fixtures stay stable across commits.
- Use **obviously fake** domains (`example.com`, `example.org`, `test.invalid`). For US-style phones in examples, use fictional `555` exchanges (e.g. `+1-555-555-01xx`) or project-local placeholders.

## Standard personas (minimal set)

Use these as defaults unless the user specifies otherwise:

| id | full_name | email | locale_hint |
|----|-----------|-------|-------------|
| `person-alice` | Alice Example | alice.example@example.com | en-US |
| `person-bob` | Bob Sample | bob.sample@example.com | en-US |
| `person-chen` | Chen Testuser | chen.testuser@example.com | en-US |

Extend with `person-dana`, `person-eva`, etc., same pattern: `Givenname Samplename`, `givenname.samplename@example.com`.

## JSON shape (reference)

When emitting structured data, prefer this shape (omit or null fields the task does not need):

```json
{
  "id": "person-alice",
  "full_name": "Alice Example",
  "given_name": "Alice",
  "family_name": "Example",
  "email": "alice.example@example.com",
  "phone_e164": "+15555550100",
  "date_of_birth": "1990-01-15",
  "address": {
    "line1": "123 Example Street",
    "city": "Sample City",
    "region": "CA",
    "postal_code": "94000",
    "country": "US"
  },
  "external_ids": {
    "customer": "cust_example_alice_001"
  }
}
```

**Notes**

- Rotate the last two digits of `phone_e164` per persona (`...0100`, `...0101`, …) to avoid collisions in tests.
- Use `date_of_birth` only when age logic matters; otherwise omit.
- `external_ids` keys should match the domain of the project (Stripe id, CRM id, etc.).

## CSV / table headers

For tabular fixtures, use a stable header row:

`id,full_name,email,phone_e164,country`

## When the user asks for “many” rows

1. Start from the minimal set above.
2. Add personas by incrementing `person-` ids and varying given/family names with `Example`, `Sample`, `Testuser`, `Demo` surnames or compound given names.
3. Keep emails aligned with `id` (`dana.demo@example.com` for `person-dana`).

## Do not

- Use celebrity names, trademarked characters, or offensive strings.
- Use real area codes, real addresses, or sequences that match valid real-world ids (real SSNs, credit cards, etc.).
