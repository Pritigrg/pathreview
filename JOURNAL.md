Week 7 — Issue selection

Issue link: Issue #117 — API docs don't include example curl commands

Issue title: API docs don't include example curl commands

Tier:  Tier 1 

Problem summary:
The PathReview API documentation identifies the available endpoints, but it does not provide command-line examples showing how to call them. This makes it difficult for new contributors to quickly test the API and confirm that their local backend is working correctly. The issue primarily affects docs/API.md rather than the application’s core frontend or backend logic. A successful fix will add clear and accurate curl commands that developers can copy and run against the local API.

“Is this right for me?” checklist reasoning:
I selected this Tier 1 issue because this is my first contribution to the PathReview codebase, and I am still becoming familiar with its architecture and development workflow. The task has a focused scope because the primary file involved is docs/API.md, rather than several interconnected source-code files. I understand the basic technologies involved, including HTTP requests, API endpoints, JSON, and command-line tools, and I can verify the examples by running the application locally. The expected result is also clear and testable: each documented curl command should match a real endpoint and produce the expected API response. Based on its limited scope, defined output, and Tier 1 label, this issue is appropriate for my current comfort level.

Branch name: docs/117-add-curl-examples

Setup confirmation: App runs locally at localhost:5173

Cohort ledger:Issue added to cohort ledger


----------------

# Week 8 — Reproduction & solution planning
(Issue:#157)
**Reproduction commit link:** 
-> https://github.com/Pritigrg/pathreview/commit/90143dc

**Reproduction summary:**
I reproduced the issue by running pytest tests/unit/test_relevance_scorer.py -k partial_overlap -q. The test failed with assert 1.0 < 0.9 because the query and chunk contain all four query keywords, causing the scorer to correctly return a full-overlap score of 1.0 instead of a partial-overlap score.

**PLAN.md link:** 
-> https://github.com/Pritigrg/pathreview/blob/relevance/PLAN.md

<!-- **Walkthrough video (recommended):** [link to your Loom video, ≤2 min — recommended, not graded] -->

**Blockers or open questions:**
I am still confirming whether the corrected test should check an exact expected score, such as pytest.approx(0.5), or only verify that the score is between 0.0 and 1.0.

## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
I implemented the fix for issue #157 by updating the partial-overlap test fixture so that only two of the four query terms appear in the retrieved chunk. The reproduction and solution-planning tasks from PLAN.md are complete, and the targeted relevance scorer test now passes.

**Next steps:**
Run the complete unit test suite and project checks, open a draft pull request, request peer or mentor feedback, and address any relevant review comments.

**Blockers:**
None.