<!-- docs/rfcs/YYYY-MM-DD-short-title.md (or docs/adr/, whichever your repo uses) -->

# RFC: Selecting a Spatiotemporal Visualization Approach for Farm2Table

<!-- Decision record header. Leave Status as "Draft" while the RFC is under review.
     When your team decides, fill in the outcome and the decision date. The
     document stays where it is; this header is what makes it a record. -->

| Field | Value |
| --- | --- |
| Author | Son Thai Do Nguyen |
| Date | 2026-10-22 |
| Status | Draft |
| Decision Date | TBD |
| Deciders | Farm2Table Team and Project Partner |
| Superseded By | N/A |

## Problem and Context

Farm2Table aims to develop an interactive web application for exploring agricultural and environmental sensor data, including temperature, soil moisture, rainfall, solar radiation, and wind conditions. Users should be able to locate sensor stations, examine historical measurements, and compare environmental conditions across locations. However, presenting geographic and time-series data together in an accessible interface remains an important design challenge.

The team is currently researching visualization approaches before beginning implementation. Harbola and Coors (2021) introduced the Environmental Sensors Visual Prediction Assessment (ESVPA) platform, which combines interactive maps, historical charts, and temporal filtering. Other research focuses on searching and comparing agricultural time-series data. Farm2Table needs to determine which approach best supports its requirements and existing Ear2Earth platform.

This decision matters because the visualization approach will influence the interface structure and integration of mapping and charting components. Although still reversible, changing the design after implementation could require significant rework. Without a decision, the team risks delaying development and reducing the time available for testing.

## Options

### Option A: Map-First Dashboard

Inspired by ESVPA (Harbola & Coors, 2021), this approach uses an interactive map as the main interface. Users select sensor stations to view measurements, historical charts, and date-filtered data.

**Benefits:**
- Combines geographic and historical information.
- Makes locating and exploring sensor stations intuitive.
- Supports additional features such as heatmaps and wind visualizations.

**Costs:** Requires synchronization between maps, charts, and filters. More complex interactions may increase development and maintenance effort.

### Option B: Time-Series-First Dashboard

Inspired by Dhaliwal et al. (2023), this approach prioritizes historical charts, search tools, and data comparisons. Maps would provide supporting geographic context.

**Benefits:**
- Supports detailed historical analysis.
- Makes comparing measurements across stations easier.
- Keeps the initial interface focused on charts and filtering.

**Costs:** Geographic exploration becomes less prominent, and users may need extra steps to locate stations.

### Option C: Do Nothing

The team could continue researching without selecting an approach.

**Benefits:** Provides additional time to investigate Ear2Earth compatibility and gather partner feedback.

**Costs:** Delays implementation and may leave insufficient time for integration and testing.

## Analysis

### Usability

Option A aligns with Farm2Table's goal of geographic sensor exploration. Harbola and Coors (2021) demonstrate how maps, charts, and temporal filtering can present spatial and historical information together. Kubicek et al. (2013) similarly connect agricultural sensor locations with measurement histories.

Option B focuses on historical analysis. Dhaliwal et al. (2023) demonstrate searching and comparing agricultural time-series datasets, which could benefit users primarily interested in identifying trends.

Both approaches are useful, but Option A appears more aligned with Farm2Table's intended workflow. User preferences still require validation.

### Technical Complexity and Maintainability

Option A requires integrating maps, charts, and sensor-data queries. Keeping selections and filters synchronized adds complexity, although reusable components could simplify maintenance.

Option B emphasizes charts and filtering but could require redesign if geographic interactions become more important.

ESVPA uses technologies including D3.js, kepler.gl, Streamlit, and Python-based tools (Harbola & Coors, 2021). Farm2Table could adopt its visualization concepts without reproducing the entire system.

### Performance, Security, and Cost

Both approaches must handle historical data efficiently and follow Ear2Earth's access requirements. Performance depends on dataset sizes, API responses, and implementation choices.

No Farm2Table-specific benchmarks exist yet, so neither approach can currently be considered faster. Third-party visualization libraries may also introduce licensing and operational costs.

Option C avoids immediate commitments but increases scheduling risk.

## Recommendation and Verification Plan

I recommend **Option A: Map-First Dashboard**, inspired by ESVPA, because it supports Farm2Table's goal of exploring sensor measurements geographically. The initial implementation should focus on station selection, historical charts, and date filtering. Advanced clustering and prediction features can be considered later.

Before adopting this approach, the team should verify:

1. **Compatibility:** Confirm that Ear2Earth provides station locations and historical measurements.
2. **Correctness:** Ensure selecting a station displays its corresponding data.
3. **Filtering:** Verify that charts update correctly for selected date ranges.
4. **Comparison:** Test measurements across different stations.
5. **Usability:** Gather partner feedback through a prototype.
6. **Performance:** Measure map and chart response times using representative datasets.

These checks should occur during initial prototyping. If significant integration or usability issues arise, the team should reconsider Option B.

## Constraints

Farm2Table must respect Ear2Earth's architecture, data-access rules, and partner requirements. Third-party libraries require licensing reviews before adoption.

The ESVPA article is published under CC BY 4.0, but this does not automatically permit reuse of all implementation components.

Confidential partner information, private datasets, and credentials must not be shared in public repositories or external AI tools without authorization.

## Delegation and Validation

ChatGPT was used to help organize the RFC, summarize the research articles, compare visualization approaches, and draft the analysis and recommendation.

Since the team has not started implementation, I focused on validating the research sources and project requirements rather than running software tests. Technical compatibility and performance will be evaluated during prototyping before the team adopts the recommendation.

**Personal validation:** I reviewed Section 2.3 of Harbola and Coors (2021) to verify that ESVPA supports interactive maps, historical charts, and temporal filtering. I also compared these features with Farm2Table's requirements for sensor exploration and historical data visualization. The research supports the proposed design, but compatibility with Ear2Earth still needs to be tested.

What is assessed is in the [AI policy](https://capstone.alexulbrich.com/assignments/introduction/#ai-policy-applies-to-every-assignment).

## Decision

**Status:** Pending.

The team has not accepted or rejected this proposal. The final decision, date, and decision chair will be recorded after review.

## References

1. Harbola, S., & Coors, V. (2021). *An Interactive Platform for Environmental Sensors Data Analyses.* https://doi.org/10.5194/isprs-annals-VIII-4-W1-2021-57-2021

2. Dhaliwal et al. (2023). *A Data Discovery and Visualization Tool for Visual Analytics of Time Series in Digital Agriculture.* https://ieeexplore.ieee.org/document/10303456

3. Kubicek, P., Kozel, J., Stampach, R., & Lukas, V. (2013). *Prototyping the Visualization of Geographic and Sensor Data for Agriculture.* https://doi.org/10.1016/j.compag.2013.07.007
