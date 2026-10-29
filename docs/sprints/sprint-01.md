# Sprint Note: Sprint [1], [Farm2Table]

<!-- One page maximum. Each numbered section is graded pass/fail (20 points each).
     The evidence may be AI-generated from your repo history and board.
     Two things must be human-written: section 5, and the "shipped" sentence
     in each contribution line. Those are the parts anyone reads. -->

**Team: Farm2Table** | **Sprint dates:** | **Date submitted:**

## 1. Working Software Evidence

-Deployed URL / release tag / demo video: No working application is available yet. This sprint focused on gathering requirements, researching visualization approaches, and understanding the existing Ear2Earth platform and available sensor data. The team also identified Roundhouse as the initial location for development. A functional prototype has not yet been implemented.

-Demo video timestamps: N/A — no replacement demo video.

-CI run: N/A — no application build or CI run to report yet.

## 2. What Got Done

Everything the team finished this sprint. Each item concrete (someone could go look at it) and consequential
(the project is meaningfully further along). It does not have to be code; non-code work counts when someone can open it (the repository, an issue or ticket, your partner's system). Activity without a result does not
belong here: "worked on the API" and "researched options" are not done things.

- Board link: https://github.com/users/SonNguyenNogFug/projects/2 
- Done this sprint:
- Established Github repository
- Met three (3) times with client 
- Established interviews with target demographic
- Met project database administrators
- Figma mock-up

## 3. Top Risk and One Decision Needed

The single biggest threat to shipping (in fall, before the Definition of Shipped exists, to the term gate), and one concrete decision the team needs from the partner, the instruction team, or itself. Take the risk from the top of your `docs/risks.md`.

- Top risk: Lack of database access
- Decision needed (from whom, by when): Client’s sensor team at OPEnS lab, as soon as possible. (Our web application is intended to pull from a database built and maintained by previous students of the customer)

## 4. Contribution Lines

One line per student, three parts:
  (a) the work you owned this sprint, one or more pieces, each with a link or ID (NDA teams: IDs only);
  (b) whose work you reviewed (a pull request, a spec, a document) and the one change you asked for, named specifically ("LGTM" is not a review);
  (c) one human-written sentence: the most consequential thing you shipped, and how the team knows it works.
If a student has nothing this sprint, their line says so plainly. Mechanical changes (formatter runs, lockfile bumps,
generated files, bulk renames) are normal work but are not evidence; leave them out.

**[Aron Meraz: ]** Researched [N-Sight: Precision Nitrogen Management](https://digitalcommons.unl.edu/cgi/viewcontent.cgi?params=/context/biosysengdiss/article/1177/&path_info=IN_SEASON_NITROGEN_MANAGEMENT_LEVERAGING_DATA_VISUALIZATION_FOR_PRECISION_AGRICULTURE.pdf) and created RFC [Isolating Farm2Table from the MongoDB Document Format]([docs/rfcs/mongodb-schema-isolation.md](https://github.com/SonNguyenNogFug/Farm2Table-Capstone/blob/main/docs/rfcs/2026-10-25mongodb-schema-isolation.md))

**Evan Seip**
- owned: Completed client instructed research deliverable and coordinated interviews w/ target demographic
- reviewed: No code reviewed this sprint
- shipped: No code shipped this sprint

**Son Thai Do Nguyen**
- owned: Drafted RFC on Time-Series Data Aggregation and Downsampling 
- reviewed: No peer reviews completed this sprint.
- shipped: I put together an RFC comparing different ways to handle sensor data and recommended an approach for the team to review.

**Thao Nguyen**
- owned: Drafted an RFC on where Farm2Table stores sensor time-series data. Researched data visualization for agriculture.
- reviewed: No peer reviews completed this sprint.
- shipped: RFC draft committed to `docs/rfcs/`. Research notes on data visualization for agriculture.

**Annika Etchison**
- owned: Began Figma mock-up of dashboard page UI with partial interactivity 
- reviewed: No reviews yet this sprint
- shipped: [link to mock up](https://www.figma.com/proto/2REL5lkeKBEB62HpwxrbpH/F2T-Main-Page-rough-rough-draft?node-id=1-2&p=f&t=7nOFPfCaMuf1ltYV-1&scaling=contain&content-scaling=fixed&page-id=0%3A1)

**Branden Rodriguez**
- owned:Helped establish the Figma mock-up and researched [cloud enabled IoT crop management](https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2022.1030168/full#s4)
- reviewed:N/A
- shipped:N/A

**Decision chaired this sprint:** who drove which decision to a conclusion. Over a term everyone should appear here at least once.

- Thao Nguyen: led the team to a conclusion on three main decisions this sprint: who takes which roles on the team, the weekly meeting schedule with partner, teammates and also Ear2Earth team and the rough UI of the Farm2Table website. 

## 5. Judgment Layer (human-written, about five lines)

We learned that as a group, we need to take initiative with the project as opposed to asking the client exactly what they wanted. This was a surprise to us because we are used to being told what to do and following instructions. We began to set up interviews with farmers to test our figma mock-up, reached out to the previous group who has worked on a similar project that utilizes the same data that we are using, and will soon have our mongoDB set up with our repository.
