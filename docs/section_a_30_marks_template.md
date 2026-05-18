# Section A Template (30 Marks) - Oladeinde Bisola

## 1) Executive Summary (10 marks)

### Business context
As Head of Cybersecurity and Compliance Advisory, I manage assessment engagements where inaccurate scoping or weak client readiness can cause delivery delays and elevated risk exposure. Improving predictability of project duration and risk outcomes is essential for pricing, staffing, and client assurance.

### Research question
Which project and client factors most strongly influence cybersecurity assessment duration, delay likelihood, and risk profile?

### Three findings (insert final evidence)
1. [Duration pattern by assessment type/client profile]
2. [Delay driver with statistical evidence]
3. [Compliance/vulnerability relationship with quantitative effect]

### Recommendation
[Specific engagement planning intervention] is expected to reduce average project delay by [X days or X%] while improving quality consistency.

## 2) Professional Disclosure (10 marks)

**Job title:** Senior Manager / Head of Department, Cybersecurity and Compliance Advisory
**Organisation:** Digital Encode Limited — a Nigerian cybersecurity consulting and compliance advisory firm serving banking, fintech, telecoms, and enterprise sectors

### Technique 1 — Exploratory Data Analysis
Before I can model project duration or risk, I need to understand the baseline distribution of outcomes across the 100 engagement records in my firm's historical project database. The dataset spans multiple assessment types (PCI DSS, SWIFT CSP, ISO 27001, vulnerability assessment, and others), multiple client industries, and a range of team sizes and system scopes. EDA will reveal whether project delays are evenly distributed or concentrated in specific sectors or assessment types — a finding with direct implications for how I scope, price, and staff engagements. For example, if 80% of delay events are concentrated in government-sector ISO 27001 projects, that changes how I write the project plan and set client expectations for that segment.

**Alternative considered:** Proceeding directly to regression or classification without profiling. Rejected because undetected distributional issues in `Total duration (days)` or `Overall compliance score (%)` — such as extreme outliers from one atypical engagement — would distort all downstream models.

**Limitation:** EDA is descriptive and cannot confirm whether patterns are statistically reliable without formal tests.

### Technique 2 — Data Visualization
Cybersecurity project performance reporting at Digital Encode is presented to the Associate Director and client portfolio leads through dashboards and visual summaries. Visualizing engagement duration by assessment type, compliance scores by client maturity level, and vulnerability counts by industry allows me to communicate risk concentration patterns in a format that non-technical management can act on. The charts produced in this analysis will be directly applicable to internal portfolio reviews and to client-facing engagement reports where I present aggregated project benchmarks.

**Alternative considered:** Presenting findings through written summary tables only. Rejected because tables obscure the distributional shape of duration and risk outcomes, which is precisely what management needs to see to make resourcing decisions.

**Limitation:** Visual patterns can overstate or understate effects relative to formal tests. All visualizations are paired with hypothesis test results before drawing operational conclusions.

### Technique 3 — Hypothesis Testing
My team regularly makes informal claims: government-sector clients cause longer delays; ISO 27001 engagements generate more vulnerabilities than PCI DSS; larger organizations take longer to achieve compliance. These claims directly influence how we price and resource engagements, yet they have never been formally tested. Hypothesis tests — ANOVA across assessment types, t-tests by client industry group, chi-squared on delay frequency by delivery mode — replace tribal knowledge with evidence. A statistically significant result in any of these tests gives me a defensible basis for adjusting our engagement playbook and pricing model.

**Alternative considered:** Reporting only descriptive mean differences without formal testing. Rejected because policy decisions based on chance variation have repeatedly led to under-resourced projects and margin erosion.

**Limitation:** With 100 records split across approximately 5–6 assessment types and client industries, some groups have 15–20 observations — below the ideal 30 for ANOVA. Welch correction and Kruskal-Wallis non-parametric tests will be reported alongside parametric results.

### Technique 4 — Correlation Analysis
I hypothesize that `Client responsiveness level`, `Security maturity of client at project start`, and `Number of systems and/or applications in scope` are the primary predictors of both `Total duration (days)` and `Number of vulnerabilities identified`. Before building regression models, correlation analysis formally maps these dependency structures and identifies any strongly collinear predictor pairs (e.g., `Number of consultants` and `Total duration` are likely correlated). This prevents me from entering multicollinear variables into regression, which would produce unstable and misleading coefficient estimates.

**Alternative considered:** Running an all-variable regression without prior screening. Rejected because multicollinearity between project size indicators would inflate standard errors and make individual coefficients uninterpretable.

**Limitation:** Correlation measures linear association only. Non-linear effects — for example, a threshold effect where very low client responsiveness causes disproportionately long delays — will not be fully captured.

### Technique 5 — Multiple Regression
The commercial purpose of this analysis is a project duration and risk-score prediction model that my team uses at the engagement kick-off stage. A regression equation that takes `Type of cybersecurity assessment`, `Client responsiveness level`, `Number of systems in scope`, `Security maturity at project start`, and `Project delivery mode` as inputs and predicts `Total duration (days)` provides a realistic timeline estimate before resources are committed. A second regression with `Number of critical/high vulnerabilities` as the outcome supports risk-based pricing — higher-risk profiles justify higher fees and more senior consultant allocation.

**Alternative considered:** Decision tree or random forest models. While potentially more accurate, tree-based models do not provide the coefficient-level interpretation required to justify a pricing adjustment to clients or to the Associate Director.

**Limitation:** With 100 observations and up to 6 predictors, the model meets the 10-per-predictor threshold but is at the lower boundary. Results should be interpreted conservatively and cross-validated where possible.

---

## 3) Data Collection & Sampling (10 marks)

- **Source:** Internal structured survey cross-referenced with historical project records maintained by Digital Encode Limited's project management function
- **Survey instrument:** Google Forms — designed by the student to capture project-level attributes and outcome metrics retrospectively
- **Primary dataset:**
  - `cybersecurity_assessment report_report_dig_enc_ltd.csv` — 100 project-level records; 17 variables: Timestamp, Type of cybersecurity assessment, Client identifier, Project delivery mode, Client industry, Approximate client organisation size, Years of Assessment/Project, Total number of consultants on the project, Number of systems and/or applications in scope, Approximate number of meetings held with the client, Client responsiveness level, Security maturity of client at project start, Total duration of the project (days), Did the project experience delays?, Overall compliance score (%), Total number of vulnerabilities identified, Number of critical/high vulnerabilities
- **Collection method:** A structured internal survey was designed to capture project-level attributes and outcomes. Cybersecurity consultants and relevant client project team members completed the survey retrospectively for engagements in the company's project records. The survey was administered by the student and approved by the Chief Project Manager and Associate Director of Digital Encode Limited before distribution. Survey responses were collected via Google Forms and exported to CSV.
- **Period covered:** 2023 – 2026 (project year field; Timestamp column confirms survey completion dates within this range)
- **Sample frame:** All completed cybersecurity compliance assessment projects handled by Digital Encode Limited in the period, as reported by project team members with direct access to engagement records. No projects were deliberately excluded, though retrospective recall limitations may mean some older or smaller engagements are under-represented.
- **Sample size:** 100 project records, 17 variables. Meets the CS1 minimum exactly (100 observations, 5+ variables). [CONSIDER: If 5–10 additional records from 2022 or early 2023 engagements can be sourced, adding them would improve the statistical power margin for ANOVA group tests where subgroup sizes are currently 15–20.]
- **Statistical justification:** With 100 records and approximately 5–6 assessment type or industry subgroups, average group sizes are 15–20 observations. This is sufficient for hypothesis testing with appropriate corrections (Welch t-test, Kruskal-Wallis) and regression with up to 6 predictors (100/6 ≈ 16.7, meeting the 10-per-predictor guideline). Results for subgroup comparisons will be interpreted with explicit power caveats.
- **Ethical notes and confidentiality:** All Personally Identifiable Information (PII), client-identifying information, and sensitive operational details were removed or altered prior to analysis. The `Client identifier` field uses coded references — no actual client names appear in the dataset. Survey participation was voluntary; no individual is identified in any analysis output. The dataset is used solely for this academic assessment at Lagos Business School and will not be commercially distributed. Approved for academic use by the Chief Project Manager and Associate Director of Digital Encode Limited.
