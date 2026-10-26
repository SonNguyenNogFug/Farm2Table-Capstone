# RFC: Where Farm2Table stores sensor time-series data

| Field | Value |
| --- | --- |
| Author | Thao Nguyen |
| Date | 2026-10-25 |
| Status | Proposed |
| Decision Date | (fill when decided) |
| Deciders | Whole Team, Team Partner |
| Superseded By | n/a |

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

| Option | Code reuse | New hosting | Reversibility |
| --- | --- | --- | --- |
| A. Mongo time series | High | None | High |
| B. TimescaleDB | Low | Yes | Low |
| C. Do nothing | Full | None | n/a |

**Performance.** One document per reading means a season-long plot scans many small documents. MongoDB's documentation says time series collections group readings into buckets to save space and speed up range queries, and TimescaleDB's documentation makes a similar claim for its tables. ([MongoDB docs: About Time Series Data](https://www.mongodb.com/docs/manual/core/timeseries/timeseries-bucketing/))

**Complexity and maintainability.** Option A changes how data is stored but keeps the same database. Options B adds a second technology while we are also building the map, plots, and onboarding. 

**Security and cost.** A and C need no new servers. B need hosting, backups, and a second set of credentials. Missing readings, mixed units, and time zones need handling in our API under every option, so the database choice affects speed more than correctness.

## Recommendation and Verification Plan

Stay with **Option C (do nothing)** if it meets the targets below. If it misses, move to **Option A**. Choose B only if A also fails. This keeps the partner's database and the lowest risk. In every case, the API reads data through one function, `getSeries(station, variable, from, to)`, so a later move does not touch the plotting code.
 
How the team will know it worked, checked before the plotting features are finished:
 
- [ ] A 30-day, 3-station, 2-variable query returns in under 1 second at the 95th percentile.
- [ ] A season plot sends the browser at most 1000 points per series.
- [ ] A CSV export matches the plotted values, including gaps and time zones.
- [ ] Any migration is rehearsed on a copy, with row counts compared before and after.
      
Rollback: keep the old collection read-only for two weeks after any switch.

## Constraints
- **Licensing:** confirm Ear2Earth's license and the license terms of any database we self-host. [Verify against current license text.]
- **Data use and partner confidentiality:** the sensor data belongs to the partner. Use only data approved for a graded document, and never commit raw data or credentials.
-  **IP:** our contributions follow the course and partner agreement.

## Delegation and Validation

- **What you handed to AI tools** I used AI to draft and summarize the MongoDB and TimescaleDB documentation.
- **What checks made that reasonable**: 
- **Where you stopped and validated the result yourself, and why those points.** 

## Decision

Proposed, until your team decides. Then accepted, rejected, or superseded, with the date and who chaired the decision. If superseded, link the RFC that replaces this one.
