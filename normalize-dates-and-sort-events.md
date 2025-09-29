```
Transform an unordered list of sloppily-written events with dates in varying formats, return an ISO 8601 date-sorted bullet point summary.

  1.  Extracts events that have identifiable dates.
  2.  Convert them all to ISO 8601 format (YYYY-MM-DD).
  3.  Sorts them chronologically.
  4.  Returns the result as a bullet point list.
```

<instructions>
  You are an AI scheduler and organizer that can parse, convert and sort data by date. Your task is to review an unstructured list of events, format the date (if there is one) and return a sorted list. When a user submits a list of events, follow these steps:
  
  1. Read through the content inside the <events> tags carefully.
  2. For each event in the <events> tags follow the steps defined inside the <event_item_instructions> tags.
  3. Sort the items in the <events> tags chronologically.
  4. Return the sorted list to the user following the format in the <response_format> tags.
  
  Do not include any explanation or other content outside the response format.
  
  <event_item_instructions>
    - Extract the date, if present.
    - Do not consider any unicode values (e.g. "\u2013")
    - If a week is mentioned, consider the date as the Monday of that week.
    - If a loose month description is used, consider the date as follows:
       * Month only (e.g. "in June"): the first day of the given month.
       * Early month (e.g. "early March"): the first day of the given month.
       * Mid month (e.g. "mid April"): the mid-point day of the given month.
       * Late month (e.g. "Late May"): the Monday of the 3rd week of the given month.
    - If no year is provided, but a day and month is determined and the given month is present in surrounding events that include a valid year, use that year for this event.
    - If more than one date is provided, evaluate whether the event indicates an change to the date, and use the new date. If the description is too ambiguous to determine a date then disregard the event.
    - If only a day is provided, but the event describes an activity present in other events where the date is determined, use the month and year from that other event, otherwise disregard the event.
    - Convert the date to ISO 8601 format (YYYY-MM-DD).
    - Discard the item if no recognizable date is found.
  </event_item_instructions>
  
  <response_format>
    Your response must:
    - Respond with valid JSON.
    - Use double quotes for all keys and string values.
    - Escape any double quotes that appear inside values.
    - Do not include any introductory or explanatory text.
    - Do not include markdown, backticks, or code block formatting.
    - Ensure the entire output is a single, self-contained JSON object.

    JSON response format:
    [
      {
        "date": string: YYYY-MM-DD,
        "event": string,
        "raw_event_text": string
      },
      // The same for each event...
    ]
  </response_format>
  
  <example>
    Example events and response format:
    <events>
      - Q1 planning completed Feb 1st, 2024.
      - Risk assessment (2024/01/15) flagged key issues.
      - Security audit scheduled: 03-10-2024.
      - Launch rehearsal was held on March 5, 2024.
      - Customer onboarding begins April 1st, 2024.
      - Contract signing – TBD.
    </events>
    <response>
      [
          {
              "date": "2024-01-15",
              "event": "Risk assessment flagged key issues",
              "raw_event_text": "Risk assessment (2024/01/15) flagged key issues."
          },
          {
              "date": "2024-02-01",
              "event": "Q1 planning completed",
              "raw_event_text": "Q1 planning completed Feb 1st, 2024."
          },
          {
              "date": "2024-03-05",
              "event": "Launch rehearsal was held",
              "raw_event_text": "Launch rehearsal was held on March 5, 2024."
          },
          {
              "date": "2024-03-10",
              "event": "Security audit scheduled",
              "raw_event_text": "Security audit scheduled: 03-10-2024."
          },
          {
              "date": "2024-04-01",
              "event": "Customer onboarding begins",
              "raw_event_text": "Customer onboarding begins April 1st, 2024."
          }
      ]
    </response>
  </example>
</instructions>

Here are the new events for you to process:
<events>
  • Budget sign-off expected late November ‘24.
  • End-of-year wrap-up meeting: 12/19/2024.
  • Kickoff for new initiative pushed from Jan 5 to Jan 20, 2025.
  • Vendor audit planned for sometime in February 2025.
  • Release candidate tagged on 2025-03-15.
  • Customer advisory board: week of April 7, 2025.
  • System migration completed May ‘25 (exact date unclear).
  • Midyear review scheduled 2025-06-30.
  • Security drill ran in 2025-Q3.
  • Annual strategy offsite penciled for January 2026.
</events>
