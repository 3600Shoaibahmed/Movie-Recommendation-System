# GitHub Copilot, extend my project with these new features:
# 1. Add a Decision Tracker:
#    - Extract sentences from the transcript that mention decisions.
#    - Look for keywords like "decided", "approved", "agreed", "finalized", "concluded".
#    - Return them as a list of decisions.
#
# 2. Improve Action Items:
#    - Detect sentences with action words like "will", "must", "should", "assign".
#    - Try to capture the **owner** of the task (the name before the keyword).
#    - Return action items as a list of dictionaries with "task" and "owner".
#
# 3. Modify `summarizer.py`:
#    - Implement `extract_decisions()` and a smarter `extract_action_items()`.
#    - Update `process_transcript()` to include `decisions` in the response JSON.
#
# 4. Update `main.py`:
#    - Ensure the `/summarize` API endpoint now also returns "decisions".
#
# 5. Update `frontend/app.py` (Streamlit):
#    - Display decisions under a 📌 "Decisions" section.
#    - Display action items with both "task" and "owner".
#    - If no decisions are found, show "No major decisions detected."
#
# Goal: After upload of transcript, UI should show summary, smarter action items, decisions, and sentiment.
