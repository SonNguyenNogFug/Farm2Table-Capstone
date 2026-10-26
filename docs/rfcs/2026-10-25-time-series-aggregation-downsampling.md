<!-- docs/rfcs/YYYY-MM-DD-short-title.md (or docs/adr/, whichever your repo uses) -->

# RFC: Selecting a Time-Series Data Aggregation and Downsampling Strategy for Farm2Table

<!-- Decision record header. Leave Status as "Draft" while the RFC is under review.
     When your team decides, fill in the outcome and the decision date. The
     document stays where it is; this header is what makes it a record. -->

| Field | Value |
|---|---|
| Author | Son Thai Do Nguyen |
| Date | 2026-10-25 |
| Status | Draft |
| Decision Date | TBD |
| Deciders | Farm2Table Team and Project Partner |
| Superseded By | N/A |

## Problem and Context

Farm2Table aims to visualize agricultural sensor data, including soil moisture, temperature, rainfall, and wind conditions. Users should be able to explore historical measurements, compare stations, and identify environmental patterns.

Sensors reportedly transmit measurements approximately every five minutes, producing around 8,640 readings per sensor over 30 days. Displaying every measurement across multiple stations could affect performance.

The team must decide how to reduce the amount of data displayed without losing important information. This decision is currently reversible, but changing the aggregation strategy after APIs and visualization components are implemented could require significant rework.

Without a strategy, the application may become inefficient when displaying long time ranges or may incorrectly represent environmental changes.

## Options

### Option A: Return Raw Measurements

Retrieve and display all original sensor readings.

**Benefits:** Preserves complete measurement details, requires minimal processing, and simplifies verification.

**Costs:** Large datasets may increase network usage, loading times, and browser rendering overhead.

### Option B: Fixed-Interval Aggregation

Group measurements into intervals such as 15 minutes, one hour, or one day.

**Benefits:** Reduces data volume, simplifies historical visualization, and is relatively easy to implement.

**Costs:** May hide sudden changes. Different variables require different calculations, such as temperature averages or rainfall totals.

### Option C: Adaptive Downsampling

Automatically adjust data resolution based on the selected time range or chart size.

**Benefits:** Balances performance and detail, supports different time ranges, and improves flexibility.

**Costs:** Requires more complex processing and testing to ensure important measurements remain visible.

### Option D: Feature-Preserving Downsampling

Select representative measurements while preserving significant peaks, drops, and changes.

**Benefits:** Maintains important environmental patterns while reducing unnecessary data points.

**Costs:** More difficult to implement and validate, especially because different sensor types have different characteristics.

## Analysis

### Data Accuracy

Option A preserves all readings but may become inefficient for long-range visualizations. Option B provides a simpler solution, although averaging measurements could hide important events.

Option C adjusts resolution dynamically, while Option D focuses on preserving significant changes. Both offer advantages but require additional validation using real agricultural data.

Aggregation must also reflect sensor meaning. For example, rainfall increments may require summation rather than averaging.

### Technical Complexity and Maintainability

Option A is easiest initially. Option B introduces straightforward aggregation logic, while Options C and D require more sophisticated algorithms and testing.

Using a reusable backend processing module would allow Farm2Table to change aggregation methods without rewriting its visualization components.

### Performance, Security, and Cost

A 30-day period contains approximately 8,640 measurements per sensor at five-minute intervals. Hourly aggregation would reduce this to approximately 720 displayed points.

However, query performance also depends on database structure and API implementation. No Farm2Table-specific benchmarks are available yet.

All approaches must follow the partner's data-access restrictions. Processing and infrastructure costs remain uncertain until the team evaluates the existing system.

## Recommendation and Verification Plan

I recommend **Option B: Fixed-Interval Aggregation** for the initial implementation because it balances simplicity, performance, and maintainability.

Proposed resolutions:

| Time Range | Resolution |
|---|---|
| 24 hours | Raw measurements |
| 7 days | 15-minute intervals |
| 30 days | Hourly intervals |
| One season | Daily intervals |

These values are preliminary and require testing.

The team should verify:

1. **Correctness:** Compare aggregated values against raw measurements.
2. **Performance:** Measure API response times and transferred data sizes.
3. **Event Preservation:** Ensure significant rainfall and soil-moisture changes remain visible.
4. **Missing Data:** Check that unavailable readings are handled correctly.
5. **Visualization:** Compare raw and aggregated charts.
6. **Export:** Ensure CSV exports correctly identify raw or aggregated measurements.

If fixed intervals hide important information or perform poorly, the team should reconsider Options C or D.

Raw measurements should remain accessible so the decision can be reversed without losing data.

## Constraints

Farm2Table must respect Ear2Earth's existing infrastructure and partner requirements.

**Data Ownership:** Original sensor measurements belong to the partner and should not be modified without authorization.

**Licensing:** External processing libraries must have compatible licenses.

**Data Quality:** Missing, delayed, or irregular readings require appropriate handling.

**Confidentiality:** Private sensor data and credentials must not be exposed publicly or shared with unauthorized AI tools.

The solution must remain compatible with the existing MongoDB API and available infrastructure.

## Delegation and Validation

ChatGPT assisted with organizing the RFC, comparing aggregation strategies.

The team has not implemented or benchmarked these approaches, so the recommendation remains provisional.

**Personal validation:** The estimated measurement counts were calculated using the reported five-minute sampling interval. The proposed time ranges were compared with Farm2Table's project requirements. Actual performance, accuracy, and API compatibility have not yet been validated.

The team will evaluate these assumptions using representative sensor data before making a final decision.

## Decision

**Status:** Pending.

The team has not accepted or rejected this proposal. The final decision, date, and decision chair will be recorded after review.
