# Expense Review Tool

A browser-based prototype for screening an expense ledger before a human review. It takes a CSV, flags transactions that meet predefined conditions, and creates a downloadable review memo with a suggested follow-up for each flag.

## Try it

Download `Expense_Review_Demo.html` and open it in a browser. The sample review runs automatically. Change the review limit and click **Run review** to see how the results change. To try a different ledger, expand **View or replace the sample CSV** and paste data using the same four column names.

## The three checks

| Check | What triggers it | What the reviewer should do |
| --- | --- | --- |
| Duplicate invoice | Another row has the same vendor and invoice ID | Compare the source invoices and payment records |
| Missing approver | The approver field is blank | Find the approval record and check who authorized it |
| Above review limit | The amount is strictly greater than the selected limit | Check whether the expense required additional approval |

## Example result

The demo uses 15 fictional transactions. At a $500 limit, it flags six transactions and records seven findings. One $925 expense has two findings because it exceeds the limit and has a blank approver field. A $500 expense stays clear, while a $500.01 expense crosses the threshold.

Two rows share the same vendor and invoice ID and both are flagged. A third invoice from that vendor has the same dollar amount and a different invoice ID. It stays clear under the duplicate rule.

## Implementation and limitations

The tool runs in a single HTML file with plain JavaScript. Rules produce the findings and the memo uses those results directly, so the output is reproducible. The demo runs locally and uses fictional data. An exception is a prompt to inspect supporting records. The tool cannot verify approvals or establish that a payment was improper.

AI assistance was used to create and test the prototype. The demo uses explicit rules and has no live language-model integration.
