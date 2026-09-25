# Student Schedule Grouping with Python

A scheduling and group assignment tool for education programs. Given a roster with meeting availability and preferred partners, it proposes groups that share a feasible time while respecting group-size targets and preferences where possible. The final assignment is presented for human review.

## Inputs and outputs

- Input: a CSV of student availability and partner preferences, with configurable column names and group limits. [Sample roster](SAMPLE_Roster.csv).
- Output: proposed groups, shared meeting times, and an assignment to inspect before use.

## How it works

The algorithm prioritizes students and time slots with fewer options, represents partner preferences as connections, and tries to retain mutual preferences. If constraints conflict, it relaxes weaker preferences and retries. It may fall back to the best feasible attempt, so users should inspect the result and make adjustments for context the input does not capture. The method adapts an [availability grouping approach](https://stackoverflow.com/questions/67391919/algorithm-to-group-people-together-based-on-their-available-timeslots-calendar).

## Start here

1. Open [Group_Generator.ipynb](Group_Generator.ipynb) and follow the prompts for the roster and constraints.
2. Inspect [BLACK_BOX.ipynb](BLACK_BOX.ipynb) for the grouping functions and implementation detail.
3. Review the proposed groups before contacting participants or treating the schedule as final.

The sample file is provided for demonstration. Use appropriate care with real student data and avoid committing identifiable rosters to a public repository.
