# Historical-Re-Scoring-of-Churn-Risk-for-B2C-Telecom-Customers

ackground:
A national telecom provider uses churn risk scores to proactively engage at-risk B2C customers via call campaigns. Scores are computed daily via a batch pipeline that:

Ingests usage, complaint, and billing data.

Applies business-defined churn scoring rules.

Publishes the scores via Kafka to both Salesforce (for CSR visibility) and a dialer call file.

Challenge:
Over time, the churn scoring rules changed (e.g., different thresholds, new behavioral inputs like app usage or survey sentiment). However, for auditability, retraining models, and fixing past data bugs, the pipeline needed to:

Reprocess historical data accurately using the rules that were valid at the time.

Ensure idempotency (multiple runs don’t create duplicates or conflicting entries).

Always resolve each record to the correct Salesforce Contact ID (even if the subscriber changed addresses or numbers over time).
