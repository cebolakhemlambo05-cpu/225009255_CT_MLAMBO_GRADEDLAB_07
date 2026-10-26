# Part A ChatGPT Transcript (Part A excerpts)

Date: 26 October 2026

This transcript records the Part A-related prompts and response excerpts from the conversation. The first message supplied the lab brief; its separate “My request” field was blank.

Prompt 1

User: Supplied the graded lab brief. The brief permits ChatGPT in Part A and lists A1–A4: load tasks, case-insensitive search, status update, and open-task count.

 Response 1

Assistant: “The brief permits ChatGPT only for Part A. It explicitly prohibits generative AI during Parts B and C including help with the Service Tickets code and answers. I can’t inspect or modify those parts for you. I can help with Part A once the Campus Tasks project is available in the workspace.”



-A1 — Task loading: Read the array from `response.data.tasks` checking it is an array before returning it.
-A2 — Task search: Convert both the query and each task title to lowercase before matching.
-A3 — Task status: Map over the tasks, toggle the status only when the ID matches and return new objects so React sees the state change.
-A4 — Open-task count: Count records whose status is `'open'`.




