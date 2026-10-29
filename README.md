# Swiggy Order Quality & Refund Analyzer

AlmaBetter Module 1 capstone by Aditya Siddaarth. Python/Pandas analysis of fictional training data, not actual Swiggy customer records.

[Open the completed Google Colab notebook](https://colab.research.google.com/drive/1a20PGrjdQQwha85LRlU9BF7RODti2PAP)

## Purpose

Bring order, refund and complaint histories into one order-level investigation report so Customer Support, Delivery Operations, Refund Operations and Restaurant Operations can prioritize follow-up.

## Run

1. Open the notebook in Colab and make a copy if you want to edit it.
2. Select **Runtime → Restart session and run all**.
3. Setup retrieves the supplied training-data ZIP and extracts `orders.csv`, `refund_requests.xlsx` and `customer_complaints.json` when absent. If the source becomes unavailable, upload those three extracted files to the runtime.
4. Inspect milestone outputs, the final scorecard and investigation controls.
5. Use the download buttons for `swiggy_order_quality_report.csv` and `swiggy_issue_summary.xlsx`.

The inputs are provided through [AlmaBetter's student-resource folder](https://drive.google.com/drive/folders/1cO6oOEPAn8QDk_kLIdPVu--cvEode5Ki). Original datasets are not republished in this repository.

## Ten milestones

1. Inspect raw order structure, counts and missing values.
2. Load and inspect refund and complaint records.
3. Standardize order identifiers, dates, statuses, amounts and timing.
4. Clean request histories and retain relationship exceptions.
5. Measure delivery delay and wrong-order flags.
6. Aggregate refunds before joining to orders.
7. Analyze complaint categories, unresolved cases and repeat contacts.
8. Validate one-to-one joins and source-count reconciliation.
9. Assign support priorities from four explicit signals.
10. Export reports, restaurant summaries and computed findings.

## Business rules

- Delivery delay is actual minus promised minutes, only for Delivered orders with valid durations. The late signal is strictly **greater than 15 minutes**.
- Other signals are the order's wrong-order flag, at least one Pending/Failed refund, and more than one complaint for the order.
- High priority: at least two signals. Medium: one. Low: zero observed signals.
- Missing timing is reviewed separately; it is not treated as on time.
- Requested/Approved refunds and wrong-order complaint text remain visible but do not silently redefine the prescribed priority signals.

## Verified results

- 5,000 orders retained, each exactly once.
- 1,265 mapped refunds plus 35 unmatched requests reconcile to 1,300 source records.
- 1,458 mapped complaints plus 42 unmatched complaints reconcile to 1,500 source records.
- 2,038 of 4,168 measurable delivered orders (48.90%) exceeded the promise by more than 15 minutes.
- 433 High, 2,196 Medium and 2,371 Low priority orders.
- 35 delivered orders need timing review.
- Unchanged automated assessment: **100/100** after restarting the session and running all cells. This is a learning scorecard, not a final human grade.

## Validation and limitations

The notebook preserves raw frames, checks unique keys and validated joins, tests the strict delay threshold and priority boundaries, reconciles related-record counts, handles no-match searches, and reads exported files back to verify totals. It includes separate orphan and manual-review tables.

Invalid dates and unavailable durations remain missing. All data is synthetic. Small restaurant samples do not establish persistent performance problems. Low priority means no observed rule-based signals, not verified absence of problems. The workflow does not process refunds or contact customers.

## Presentation

An 18–20 minute recording guide is included in the notebook. The learner's explanation video is pending; no video link has been fabricated.

## Environment

Python 3, pandas, NumPy, openpyxl, gdown, ipywidgets and IPython. Google Colab supplies the runtime and download integration. No external AI API or machine-learning model is used.
