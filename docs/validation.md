# Evidence and validation scope

Reviewed on **5 November 2026**.

| Check | Status |
|---|---|
| Original product announcement and all four gallery screens | Reviewed in LinkedIn |
| Public application snapshot | Reviewed at `22e66e25c2d89fc72fe989534a9c8aa11758eaf1` |
| FastAPI account/tenant/campaign/lead code and client mappings | Inspected |
| Qwen setup, generation modules, source connectors, and senders | Inspected |
| New showcase documentation links | Checked against the reviewed source and local document paths |
| Full original application setup, provider calls, database access, and sending | Not run |
| Production throughput, costs, uptime, delivery, or conversion metrics | Not verified |

## Before claiming reproducibility or production guarantees

1. Restore the complete application tree. The visible source imports database configuration
   and model modules that are absent from the visible top-level tree.
2. Verify that every generation path receives the intended model and fails explicitly when
   it is unavailable. The shared registry and the standalone generation-module references
   need an integration check.
3. Isolate identity per UI session and test two organizations concurrently. Check every
   campaign/lead route for cross-tenant reads and writes, not only the obvious list route.
4. Trace imported/scraped batches through normalization, committed API rows, local export
   fallback, and retry. Prove that a partial upload or repeated send cannot create hidden duplicates.
5. Test sender rejection, timeout, retry, and recovery with synthetic contacts and blocked
   real delivery. Confirm receipts separately for acceptance, delivery, and engagement.
6. Evaluate personalization on factual consistency, relevance, review effort, and failure
   cases. Compare cold/warm generation timings and actual operating cost under stated conditions.

Source inspection establishes implementation details. A UI screen establishes the presented
interface. Operational results require their own records and measurement method.
