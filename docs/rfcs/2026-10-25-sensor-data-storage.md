# RFC: Where Farm2Table stores sensor time-series data

| Field | Value |
| --- | --- |
| Author | Thao Nguyen |
| Date | 2026-10-25 |
| Status | Proposed |
| Decision Date | (fill when decided) |
| Deciders | (who agreed to the outcome) |
| Superseded By | (link, if applicable) |

## Problem and Context
 
We must decide where Farm2Table stores sensor readings. Ear2Earth, the platform we build on, uses MongoDB. Our main features (plots from 24 hours to a full season, comparing stations, CSV export) all depend on how fast we can read a time range.
 
This is hard to reverse. Once the API, plots, and export are built on one storage design, changing it means migrating data and rewriting queries. Deciding now is cheap, and deciding after those features ship is not.
 
The partner may treat MongoDB as part of the inherited stack. So this RFC also asks what we would need to prove before asking the partner to reconsider.
 
If we do nothing, we keep the current schema. That may be fine, but we have not yet tested it on long ranges.
 
## Options
 
### Option A: MongoDB time series collections
 
Same database, but readings use MongoDB's built-in time series storage. 

Benefits: most code and tooling carry over, no new hosting, and we can export and reload data if we back out. 

Costs: a schema change and a data migration. This is the right choice if the current schema misses our speed targets but MongoDB is still acceptable to the partner.
 
### Option B: PostgreSQL with TimescaleDB
 
A relational database built for time series, with PostGIS for map queries. 

Benefits: strong range queries and mature geospatial support. 

Costs: a second technology to learn and host, and a rewrite of the data layer. This is the right choice if Option A also misses the targets, or if we need relational joins MongoDB cannot do.
 
### Option C: Do Nothing
 
Keep the current MongoDB collections. 

Cost: season-long plots and multi-station comparisons may be slow, and we would find out late, after the plotting code depends on it. This is the right choice if our measurements show current queries already meet the targets below.

## Analysis

The technical tradeoffs that matter for this decision: performance, complexity, maintainability, security, cost. Argue from evidence (benchmarks, prototypes, documentation, prior art) and cite what you relied on so a reviewer can check it. Acknowledge what you are uncertain about.

## Recommendation and Verification Plan

Which option you propose and why it wins the analysis above. Then, concretely: how will the team know it worked? List the tests, metrics, or acceptance criteria that would detect failure, and when they will be checked.

## Constraints

Licensing, data use, IP, and the partner confidentiality boundary as they bear on this decision. If none apply, say so explicitly and briefly explain why.

## Delegation and Validation

- **What you handed to AI tools** on this decision, whether that was the analysis, the prototype, the tests, or the writing.
- **What checks made that reasonable**: tests, CI, review gates, a staging environment, a rollback path. Name the ones that actually exist in your repo, not the ones you intend to build.
- **Where you stopped and validated the result yourself, and why those points.** If this decision is hard to reverse, say what you personally checked before committing to it.

What is assessed is in the [AI policy](https://capstone.alexulbrich.com/assignments/introduction/#ai-policy-applies-to-every-assignment).

## Decision

Proposed, until your team decides. Then accepted, rejected, or superseded, with the date and who chaired the decision. If superseded, link the RFC that replaces this one.
