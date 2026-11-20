# log.md, session 3, Lyon and Paris

Every AI interaction, in order, not edited afterwards. Code is in notebook_s3.ipynb.

Model A: [exact name and version]
Model B: [exact name and version]

## Framing

v1 = system_prompt.md + context_note.md (columns and units only).
v2 = same + the business rules at the end of context_note.md, added after round 1 because [...].

Checked against the slides: role (1st line), checkable rules (1 to 5), visible data loss (rules 2 and 3), named output (a, b, c), business question, what a row is, meaning + unit of each column, no data pasted.

## Lyon

Baseline (session 2): 7,000 raw rows, 407 missing end station kept and flagged (397 left after the duration filter, 10 of them also had a bad duration), 3 labels, 109 negative and 96 trips of 24h+ removed, 6,795 rows, 160 IQR outliers flagged (fences -7.9 and 36.1).

Task prompt, same for both models and both rounds:
> Audit trips_lyon.csv, list the problems you find, then write pandas code that cleans the file. Handle outliers and report the final row count.

### Round 1 (framing v1)

#### Entry 1, Model A: [name and version]
System prompt: v1
Context note: v1
Prompt: task prompt above
Output:
```python
[model code, as is]
```
```
[what it printed]
```
Audit: [what was right, what was wrong]
Correction: see fixes below

#### Entry 2, Model B: [name and version]
System prompt: v1
Context note: v1
Prompt: task prompt above
Output:
```python
[model code, as is]
```
```
[what it printed]
```
Audit: [...]
Correction: see fixes below

#### Grid round 1

| Check | Baseline | Model A | Model B |
|---|---|---|---|
| Raw rows loaded | 7,000 | | |
| Missing end_station_id | 407, kept and flagged | | |
| Vehicle labels after cleaning | 3 | | |
| Negative durations | 109 removed | | |
| Trips of 24h or more | 96 removed | | |
| Rows after cleaning | 6,795 | | |
| IQR flagged rides (k=1.5) | 160 | | |

Mismatches:
- [model, check]: [what differs] -> line: `[...]` -> why the model probably did it: [...]
- ...

If a model says one number but its table gives another, write both here.

#### Fixes

Fix 1, model [A/B], [check]
```python
# model
...
# mine
...
```
What was wrong and how I found it: [one line]

Fix 2 ...

Closest: [A/B] ([x]/7). Safest: [A/B] because [...].

### Round 2 (framing v2)

#### Entry 3, Model A: [name and version]
System prompt: v1
Context note: v2
Prompt: same task prompt
Output: [code + what it printed]
Audit: [...]
Correction: [...]

#### Entry 4, Model B: [name and version]
System prompt: v1
Context note: v2
Prompt: same task prompt
Output: [code + what it printed]
Audit: [...]
Correction: [...]

#### Grid round 2

| Check | Baseline | Model A | Model B |
|---|---|---|---|
| Raw rows loaded | 7,000 | | |
| Missing end_station_id | 407, kept and flagged | | |
| Vehicle labels after cleaning | 3 | | |
| Negative durations | 109 removed | | |
| Trips of 24h or more | 96 removed | | |
| Rows after cleaning | 6,795 | | |
| IQR flagged rides (k=1.5) | 160 | | |

What v2 changed: [...]

#### Entries 5 and 6, charts
Prompt:
> With the cleaned table, plot a histogram of durations, a boxplot of duration by vehicle type and the number of trips per hour. Add one sentence describing each chart.

| | Mine | Model A | Model B |
|---|---|---|---|
| Uses the cleaned table | yes | | |
| Title, axis names, units | yes | | |
| Median around 13 min | 13.3 | | |
| Sentence matches the chart | yes | | |

My charts: median 13.3 min, same median for the 3 vehicles, trips per hour almost flat (227 to 314), no rush hour peak. If a model writes "morning and evening peaks", it's not what the chart shows.

## Paris (mini-challenge)

Framing v2, only the file name changed (trips_paris.csv).

My baseline (session 2): [raw rows], [missing end station], [labels], [negative removed], [24h+ removed], [rows after], [IQR flagged, fences].

#### Entry 7, Model A: [name and version]
System prompt: v1
Context note: v2 with trips_paris.csv
Prompt: same task prompt with trips_paris.csv
Output: [...]
Audit: [...]

#### Entry 8, Model B: [name and version]
System prompt: v1
Context note: v2 with trips_paris.csv
Prompt: same task prompt with trips_paris.csv
Output: [...]
Audit: [...]

#### Grid Paris

| Check | My Paris cleaning | Model A | Model B |
|---|---|---|---|
| Raw rows loaded | | | |
| Missing end_station_id | | | |
| Vehicle labels after cleaning | | | |
| Negative durations | | | |
| Trips of 24h or more | | | |
| Rows after cleaning | | | |
| IQR flagged rides (k=1.5) | | | |

Differences:
- [...] -> I trust [mine / model A / model B] because [...]

Rule I would add to the framing: [...]

## Still to check

distance_km and distance_meters are the same info (km x 1000 = meters on every Lyon row), keep only one before modelling in session 4.
