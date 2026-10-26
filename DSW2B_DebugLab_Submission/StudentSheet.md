# Practice Debugging Answer Sheet

Name: Cebolakhe
Student number: 225009255

## Part A: Campus Tasks

### A1. Task loading

Cause: The record extractor must read the task array from the response's `data.tasks` property. Reading a different property does not return the bundled tasks.

File and correction: In `src/logic.cjs`, `extractRecords` reads `response?.data?.tasks` and returns the value only if it is an array. Otherwise, it returns an empty array.

Verification: The bundled response contains 3 tasks. The logic check extracted all 3.

### A2. Case-insensitive search

Cause: A case-sensitive comparison fails when the search query and task title use different capitalization.

File and correction: In `src/logic.cjs`, `filterRecords` trims and lowercases the query and lowercases each task title before matching.

Verification: An uppercase query for the first sample task returned that task.

### A3. Status update

Cause: A status update should change only the selected task and switch its status.

File and correction: In `src/logic.cjs`, `toggleRecord` maps over the tasks, returns an updated copy for the matching ID, and leaves the other task objects unchanged.

Verification: Toggling task `t1` changed its status. The other two sample tasks were unchanged.

### A4. Open-task count

Cause: The dashboard should count tasks whose status is `open`.

File and correction: In `src/logic.cjs`, `countOpen` filters for `status === 'open'` and returns the number of matching tasks.

Verification: The sample has 2 open tasks. After toggling one open task to done, the count became 1.

## Part B: Service Tickets

### B1. Ticket loading

Cause: The ticket array is nested at `data.tickets`. Reading the wrong property does not return the tickets.

File and correction: In `src/logic.cjs`, `extractRecords` reads `response?.data?.tickets` and checks that the value is an array.

Verification: The bundled response contains 3 tickets. The logic check extracted all 3.

### B2. Case-insensitive search

Cause: A case-sensitive comparison misses matches when the query and ticket subject use different capitalization.

File and correction: In `src/logic.cjs`, `filterRecords` trims and lowercases the query and lowercases each ticket subject before matching.

Verification: An uppercase query for the first sample subject returned that ticket.

### B3. Status update

Cause: Only the selected ticket should switch between `open` and `done`.

File and correction: In `src/logic.cjs`, `toggleRecord` maps over the tickets, returns an updated copy for the matching ID, and leaves the other ticket objects unchanged.

Verification: Toggling ticket `s1` changed its status. The other two sample tickets were unchanged.

## Part C: Code explanation

### C1. Inspecting the response structure

Inspect the response to find where the ticket array is stored, such as `data.tickets`. If the app reads the wrong property, it may receive `undefined` or an empty list, so no tickets will display.

### C2. Toggling one ticket and immutable updates

Map over the tickets and compare each ID with the selected ID. Return a copied ticket with the opposite status for that ID, and return every other ticket unchanged. The new array and updated object let React detect the state change and render it.

### C3. Checking the open-ticket summary

Count the tickets marked `open`, toggle one open ticket to done, and check that the displayed count decreases by one. Toggle a done ticket back to open and check that the count increases by one. The current Service Tickets `countOpen` function counts `done`, so this check exposes the summary defect. Part B does not require fixing it.

## Verification evidence

Direct Node checks against both bundled JSON fixtures passed. Each app extracted 3 records, an uppercase search found the matching record, and toggling changed only the selected record. Campus Tasks showed 2 open tasks before a toggle and 1 after.

