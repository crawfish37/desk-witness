# desk-witness

Append-only tamper-evidence anchor for a private trading desk's
certification records. Contents are SHA-256 digests only:

- `heads/` — one write-once head per recorded shakedown day file
- `beats/` — hourly heartbeat-log digests + chain head

The security property lives server-side: a protected `main` (no force
pushes, no deletions) written by a push-only deploy key. Local records
are verified against this remote before any readiness decision; a
divergence, a missing head, or a head this machine no longer has all
refuse. Nothing here is secret — the value is that it cannot be
quietly rewritten.
