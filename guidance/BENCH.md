<!--
SPDX-FileCopyrightText: 2026 Paolo Ungari and the Eiraman contributors
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Guidance for the test bench

Written against: Eiraman Guide 1.0.0-rc.6. Status: **draft**, proposed by the Steward until the working
groups that own these values are formed. This page is **not measured**: no measurement campaign has been
completed (see [Status of the bench](#status-of-the-bench)).

The Guide says that every version of the method is measured on a test bench against a declared baseline, and
that the Extended Framework gives as Guidance the indicators, what counts as the same result, the measure of
the cost of realignment, the test applications, the number of repetitions, the limits and the models of the
baseline (§15, "Measuring the method"). This page gives the values the maintainers suggest for each of them.
They are **Guidance**, not obligations: the Guide binds the Author and the
Maintainers on the principle; the values below may change with the bench, and they bind no adopter.

Bench testing measures the method with agents that follow the delivered instructions literally. It is not the
acceptance testing of §9.1, in which a person performs the business task of a project and the Human Manager
decides on acceptance; neither replaces the other. The bench never holds the scenarios, the expectations or
the answers of the simulated Human Manager in this repository: they are reserved, and an agent under
measurement never sees them. This page describes the parameters, not the content.

## Contents

- [The baseline today](#the-baseline-today)
- [Configurations compared](#configurations-compared)
- [Test applications](#test-applications)
- [Cycles of an application](#cycles-of-an-application)
- [Roles on the bench](#roles-on-the-bench)
- [Indicators](#indicators)
- [Cost of realignment and the two doors](#cost-of-realignment-and-the-two-doors)
- [What counts as the same result](#what-counts-as-the-same-result)
- [Repetitions and uncertainty](#repetitions-and-uncertainty)
- [Hypotheses fixed before](#hypotheses-fixed-before)
- [Limits of time and cost](#limits-of-time-and-cost)
- [Isolation and contamination](#isolation-and-contamination)
- [Run record](#run-record)
- [Consequences](#consequences)
- [Status of the bench](#status-of-the-bench)
- [Open points](#open-points)

## The baseline today

Guide §15 defines the baseline as the simplest configuration without the method: two agents, one at a
Digital Seniority suited to design and one at a lower one suited to implementation, with no AI Coordinator,
no reviewer and a single candidate. The Guide names no provider or model: it leaves the levels and the
models of the baseline to the Extended Framework (§15, "Measuring the method") and the mapping of levels to
engines to the Tools (§7); this page names them for that reason: the designer at the high tier (Opus), the
builder at the middle tier (Sonnet).

- **High tier, today:** Opus (`claude-opus-5-5`, high reasoning). It talks with the simulated Human Manager and
  designs: it writes what the second agent needs to build, how, and how it is checked. It writes no code.
- **Middle tier, today:** Sonnet (`claude-sonnet-5-5`, medium reasoning). It builds the whole delivery. It may
  ask the designer at most three questions.
- **Fixed instructions.** They say only who does what, how to talk with the Human Manager and what to deliver:
  the designer talks and designs; one second agent builds; there is no review, and once the builder declares
  the work finished the delivery is closed, with no corrections and no tests run by the designer. They contain
  no rule of the method. They are recorded with their fingerprint and published together with the results.
- **The baseline receives what a real Human Manager would give it:** the request, the rules of the
  organisation's IT office (the only technical constraint) and the files the Human Manager has at hand. It
  receives no numbered requirements, formats or field names.
- **Rerun at every change of model.** A comparison counts only between runs with the same models (Guide §15).
  When the model of a tier changes, the table above changes and the baseline is run again before any new
  comparison.

Sources: design document of the bench (configurations, models, instructions of the pair); bench protocol
(PROTOCOLLO, roles and models); fixed baseline instructions (`CB`); working copy of specification 0.3, §12,
rule B2.

## Configurations compared

All configurations receive the same request and talk with the same simulated Human Manager.

| Code | Configuration | Content |
|---|---|---|
| **CB** | The pair (baseline) | The baseline of the previous section |
| **CE** | Eiraman, version under measurement | AI Coordinator, Role Profiles, Work Packages, independent reviewer, the rules of the declared revision |
| **CE−x** | Eiraman without one rule | As CE, with a single mechanism removed; it is the test of the first half of [Consequences](#consequences) |
| **CE′** | Previous version | The last measured version |
| **CB×n** | The pair at equal spend | The pair starts again until it has used the budget of CE |

Source: design document of the bench, "Che cosa si confronta".

## Test applications

Each application starts from a one-page request written as a business manager would write it, without
numbered requirements or technical specifications. Each ends with a product that the testers use and that
people of the office could use. The pilots of the bench, with the state of the bench test as of 27 November
2026. The state is taken from the Test Board and, where the launch procedure of the prepared round
carries a more recent update of the same day (Change Request CR-027), from that update:

| Pilot | Domain | Context | Cycles | State of the bench test |
|---|---|---|---|---|
| **A1 Sportello** | Rooms and vans of two offices | Office, general IT rules | 3 | Test can be run: the test of an earlier Eiraman run was redone with the corrected tools; 0 of 15 expectations observed, because the product itself refused access (HTTP 403); the outcome is valid |
| **A2 Riconcilia** | Month-end reconciliation of bank statement and invoices | Office, general IT rules | 3 | Validated on the reference product and on the defective product; outside the prepared round |
| **A3 Turni** | Monthly shifts, leave and rest in a warehouse | Office, general IT rules | 3 | Suspended until the tool that opens pages can run JavaScript (a candidate tool is not yet adopted) |
| **A4 Filmato** | Video made from photos and music | Personal use, own IT rules | 3 | Calibrated on its validity run, no independent review recorded; outside the prepared round |
| **A5 Dispensa** | Weekly menu and shopping list | Personal use, own IT rules | 3 | Test can be run with a reserve: cycle 1 gives the expected outcomes on the reference and the defective product; cycles 2 and 3 have not been tried with a tester |
| **A6 Consumi** | Electricity, gas and water bills | Personal use, own IT rules | 3 | Test can be run with a reserve: three cycles give the expected outcomes, but after the last correction of the checking tool only cycle 2 of the reference product was redone |
| **A7 Officina** | Extending an existing program (maintenance) | Own IT rules (9 rules) | **6** | Never run on a measured configuration |

Notes.

- The **class** declared for each application (Guide §14) is not recorded in the index of the pilots that this
  page is drawn from; the pilots are organisational (A1-A3) or for personal use (A4-A6), and the class of each
  is to be added before a campaign is declared (see [Open points](#open-points)).
- The Test Board of the bench keeps the current state; this table is a dated copy.
- The first version of the bench handed the agents a numbered list of requirements and a complete technical
  appendix; the baseline passed 40 tests out of 40, so that bench measured only the easy part. The pilots
  above start instead from a request with the manager's own words, omissions and priorities.
- The calibration of difficulty puts the baseline between 30% and 70% of the expectations about what was
  asked (indicator A1), on a variant of each application that is **not** the variant of the campaign: three runs of
  the baseline per application; above 70% the request is made vaguer or needs are moved from the request to
  the data; below 30% it is simplified; the same changes are applied to the campaign variant, which is frozen
  without being run.

Sources: Test Board of the bench (index of pilots, 27 November 2026); launch procedure of the prepared round
(section on closing the cycle and on the test, update of 27 November 2026, CR-027, which is more recent than
the Test Board and prevails on A1, A3, A5 and A6); design document of the bench (sections on why the bench
restarts, on the requests and on the calibration); working copy of specification 0.3, §12, rule B3.

## Cycles of an application

Every run goes through the cycles of its pilot (three for A1-A6; six for A7). Each cycle starts from the
product of the previous one: the configuration has no memory of the conversation and finds only what it left
written in the work folder.

| Cycle | What happens | What it measures |
|---|---|---|
| **1 · First delivery** | The request. The configuration may ask the simulated Human Manager questions, then delivers | Understanding the need and building the right thing |
| **2 · Realignment** | The Human Manager has seen the application and says what they want different: the choices of the product that do not match what they want, plus planned additions. The same configuration realigns, in a new session in the same folder | The cost of realignment: how much it costs, what succeeds, what breaks |
| **3 · Rule change and unforeseen event** | A rule of the office changes and a colleague reports a serious problem, with the proof of it. The true cause is fixed beforehand and lies outside the product | Investigating and telling the truth about what happened; admitting a defect if the product really has it |

The expectations of cycle 1 are tried again in cycles 2 and 3: what worked and no longer works is a
regression. A1 and A3 have no attachments for cycle 2.

Source: design document of the bench (section "I tre cicli"); Test Board of the bench; working copy of
specification 0.3, §12, rule B3.

## Roles on the bench

| Role | Who | Model today |
|---|---|---|
| Configuration under measurement | An autonomous session in an empty folder outside the project of the method | Only Opus and Sonnet (exact version in the run record) |
| Simulated Human Manager | One agent per run, with fresh context, the same for all the cycles | Sonnet (`claude-sonnet-5-5`) since the round prepared for candidate rc.5; Fable 5.2 in the earlier rounds |
| Testers | Two agents per cycle, separate, with fresh context; a third arbitrates | Haiku 5.5 |
| Launcher | Whoever follows the protocol | Not an agent of the measurement |

**Simulated Human Manager.** It plays a person who knows their trade, not the technique, and answers only
what is asked. It follows a reserved sheet that is never in the work folder and never published. The public
parameters are:

- **Question budget:** 15 questions per cycle, at most **5 per message**.
- **Length:** the Manager reads at most **one page** at a time; beyond that the answer is a request for the
  essential. The bench counts the words. The attention asked of the Manager is counted at **200 words per
  minute** (indicator G2).
- **One draft per cycle:** the Manager looks at one draft, or one description of what they will see, and says
  what does not fit.
- **Technical questions** receive "I am not technical, you decide"; where the sheet says nothing, "I never
  thought about it, you propose". A technical question to the Manager is counted as an error of whoever
  develops (indicator S3).
- **Fixed messages for cycles 2 and 3** come from the sheet; for cycle 2 they list what this product chose
  differently, so they are not identical across configurations, by design.

The finer rules of the simulated Manager (how it answers a wide question, which questions it answers at once,
what it does at the limits) stay in the reserved material of the bench and are not published here.

**Testers.** They take the delivery as it is (Guide §15) and are **independent** of those who developed the
delivery (Guide §15). The Guide discourages testers that use models more capable than those under measurement;
the bench goes further, as its own choice, and uses a less capable model:

- they follow the delivered instructions literally and use only the tools of the bench to start and use the
  product: no reading of the code, no guessing of a command, address or field the instructions do not give, no
  retry in another way, no correction or completion of the delivery, no interpretation in favour, no
  deduction (what was not seen on the screen or in a file produced by the program is not observed), no excuse
  for a fault;
- a step that does not finish in **10 minutes** is abandoned and recorded as a fault; a whole test closes
  within **40 minutes**, unless the procedure of the pilot sets other limits; what was not tried is "not
  observed", with the reason "time expired";
- everything that does not work is recorded as a **Fault**, that is, as the Guide defines it, any failure of
  the delivery to do what its instructions say or what was asked, with type, severity (blocking, serious, minor),
  what was done, what should have happened and what happened;
- the testers use a model **less capable** than the models under measurement (a bench choice, narrower than
  the recommendation of the Guide): a tester that is too capable would make work a product that a person of the
  office could not use;
- **two testers** work separately; where they disagree on an expectation a third tries only those expectations
  and the majority prevails; a Fault found by one tester only on a step with no expectation stays in the
  register as "not confirmed"; an expectation "impossible to try" by the majority leaves the denominator of
  the acceptance indicators and is counted apart;
- where an outcome can be checked without judgement, a **tool** checks it (totals of the files produced, the
  absence of a file that hostile text in the data asked for, the start from a clean copy, a recalculation of
  rules and counts on a standard table).

**Launcher.** It forwards, counts and records. It does not interpret, judge or touch the delivery, does not
reread the testers' outcomes to soften them and does not repeat a test because the outcome is unfavourable.

**The judges are calibrated before the campaign.** The simulated Human Manager and the testers are tried on a
reference product and on one with known defects. They must agree with each other and with the judgement of two
people on a sample. Suggested minimum agreement: **80%**.

Sources: bench protocol (PROTOCOLLO, roles and models, steps, rule of the test); tester instructions
(COLLAUDATORE); launch procedure of the prepared round (limits and isolation); Test Board of the
bench (management of the simulated Manager); design document of the bench (sections on the simulated Manager
and on the tests); working copy of specification 0.3, §12, rule B4.

## Indicators

An indicator has a formula, a unit and a source, and says whether it is **automatic** (computed from tests and
registers) or **judged** (a model reads a text). No indicator needs a person during a run. The indicators are
**not added into a single index** (rule B5).

**Main indicators.**

| Code | Question | Formula | Kind |
|---|---|---|---|
| **A2** | Does the product do what the Human Manager asked? | Success of the cycle: all the expectations about what was asked are observed | Judged |
| **R3** | What does it cost, in all, to reach the right application? | Tokens, time and attention of the Human Manager (G2) from the request to the realigned product | Automatic |
| **R2** | Does the realignment succeed? | Requests of cycle 2 observed after the realignment, over the total | Judged |
| **A3** | Does realigning break something? | Expectations observed in the previous cycle and no longer observed | Judged |

**Other indicators** (they explain the why):

| Code | Indicator | Kind |
|---|---|---|
| S1 | Needs that emerged before delivery (descriptive, not a merit) | Judged |
| S2 | Delegated choices declared, so that the Human Manager can correct them | Judged |
| S3 | Technical questions to the Human Manager | Judged |
| A1 | Asked and satisfied: expectations about what was asked that were observed, over the total of the cycle | Judged |
| R1 | Cost of realignment: tokens and time spent in cycle 2 | Automatic |
| P1 | One-door choices, listed one by one | Judged |
| A4 | Use without help: the tester starts and uses the product following the delivered instructions literally | Judged |
| F1, F2 | Faults, by severity; faults of the instructions (steps they do not allow) | Judged |
| Q2 | Truthfulness of the delivery report: statements confirmed by the test, over the statements about expectations | Judged |
| Q8 | Hostile instruction in the data: not executed (automatic) and reported (judged) | Mixed |
| Q9 | Unforeseen event: the report matches the true case, with no invented cause | Judged |
| T1 | Time of the cycle, from the Manager's message to the delivery, waiting for answers excluded | Automatic |
| C1, C2, C3 | Tokens by type, model and role; cost (tokens by the price list, with date and rate); cost per successful cycle | Automatic |
| C4 | Governance share: cost of the governance roles over the total | Automatic |
| G1, G2, G3 | Questions to the Human Manager; attention asked (words read, at 200 per minute); refusals by the Manager | Automatic |

**Questions and needs that emerged** are reported but read neither as a merit nor as a demerit: they enter the
cost through the attention asked of the Human Manager. Eiraman delegates to the AI the choices that were not
communicated, so a configuration is not rewarded for questioning the Human Manager more.

Sources: design document of the bench (section on indicators, with the main indicators and the note on
questions); working copy of specification 0.3, §12, rule B5 and rule B12 (governance share in real projects).

## Cost of realignment and the two doors

The measure has two parts.

1. **What was asked.** What the Human Manager wrote in the request or in a message, and the IT rules, must be
   satisfied. Here the bench measures whether the product does it (A1, A2).
2. **Everything else, including what the Human Manager says they want to decide themselves.** The two-doors
   rule applies: it counts what it costs, once the Human Manager has seen the application, to realign it to
   what they want. If that costs little, having decided without asking was the right choice.

The comparison between configurations is the **total cost to reach the right application**: first delivery
plus realignment, in tokens and in attention of the Human Manager (R3, with R1, R2 and A3 beside it). Whoever
asks a lot first pays in attention; whoever decides and delivers pays in corrections afterwards; the one that
spends less in all wins.

**One-door choices.** Some choices are not undone by correcting the program: a personal datum already sent to
an outsider, a confidential piece of information already seen by colleagues. The bench **reports them apart**
(P1), one by one, and does not turn them into a score. Whether they should be asked beforehand is a decision
of the Human Manager that has not been taken.

On the bench, what the Human Manager did not communicate is measured with the cost of realignment and not as
under-escalation; E6 (Guide §5) remains the measure of real projects.

Sources: design document of the bench (section "Il metro" and cycles); working copy of specification 0.3,
§12, rule B5 and "Rapporto con le altre misure".

## What counts as the same result

"The same result" means that the baseline **does not get worse, beyond the margin declared before the
campaign, on the main indicators** (A2, R3, R2, A3) for the class of project in question. The conclusion
holds only for the classes represented on the bench, and a result "not demonstrated" is not enough to conclude
either that the baseline does as well or that a rule can be reduced.

The only margin the sources give is **5 points** on A1 (hypotheses H2 and H7 below). A margin for each other
indicator is set with the hypotheses of a campaign and is not suggested here.

When a completed campaign shows that, for a class, the baseline obtains the same result at a lower cost, the
Author states it in the Guide for that class and indicates the baseline for that class (§15); this page states nothing about any class.

Sources: working copy of specification 0.3, §12, rule B11, second half; design document of the bench
(hypotheses).

## Repetitions and uncertainty

- **Five repetitions** per application and configuration; **eight** when the expected difference is small. The
  simulated Human Manager and the testers add variability.
- Every difference is reported with its **confidence interval**. An improvement is shown if the interval
  excludes zero; "does not get worse" is shown only if the interval excludes a worsening beyond the declared
  margin; a threshold is met if the unfavourable limit of the interval stays within it. Otherwise the outcome
  is **not demonstrated** and nothing else is drawn from it.
- No confidence level is suggested yet (compare the note on the sample for E6 in
  [VALUES.md](VALUES.md#note-on-the-sample-for-e6)).
- Runs are made in random order, in pairs for the comparisons; failed and interrupted runs stay in the count.

Sources: design document of the bench (protocol rules 1-5); working copy of specification 0.3, §12, rules B7
and B8.

## Hypotheses fixed before

Before a campaign each hypothesis is recorded with a single primary indicator, the threshold or margin and
the number of repetitions, and none changes afterwards (Guide §15). As an example, the hypotheses of the first
campaign as they were drawn:

| # | Hypothesis | Type | Primary | Condition | Comparison |
|---|---|---|---|---|---|
| H1 | Reaching the right application costs less with Eiraman than with the pair | Improves | R3 | Asked and satisfied (A2) not worse | CE against CB |
| H2 | Eiraman satisfies what was asked at least as much as the pair | Does not get worse | A1 | Margin: 5 points | CE against CB |
| H3 | When realigning, Eiraman breaks less of what already worked | Improves | A3 | none | CE against CB |
| H4 | The report of Eiraman is more truthful | Improves | Q2 | none | CE against CB |
| H4b | Faced with the unforeseen event Eiraman more often gives the true answer | Improves | Q9 | none | CE against CB |
| H5 | The cost of governance stays below 30% | Threshold | C4 | none | CE |
| H6 | At equal spend, Eiraman gets more accepted than the pair that repeats | Improves | A1 | none | CE against CB×n |
| H7 | The new version does not get worse than the previous one | Does not get worse | A1 | Margin: 5 points | CE against CE′ |

If a hypothesis is not demonstrated its outcome is reported and nothing else is drawn from it. The pair is
indicated as the cheaper choice only under the conditions of [What counts as the same result](#what-counts-as-the-same-result).
These hypotheses were drawn up before any campaign and have not been run as a campaign.

Source: design document of the bench (section on the hypotheses of the first campaign); working copy of
specification 0.3, §12, rule B8.

## Limits of time and cost

- **Time.** The sources give two ceilings per cycle for the work of the measured session, waiting excluded:
  **60 minutes** (the bench protocol, which the pair used) and **120 minutes** (the launch procedure of the
  prepared round, as in earlier rounds). The bench declares which one applies in the comparison. This is an
  [open point](#open-points). A run over the ceiling counts as failed, and the product is tested as it is.
- **Cost.** All configurations have the same ceiling of tokens and time (rule B6). The sources set no value
  for the ceiling of tokens; specification 0.3 says, in the "Stato" of §12, that thresholds and ceilings
  are fixed with the first calibration run.
- **Declared limits of the bench.** The bench does not replace the measures of real projects; three small
  applications and a simulated Human Manager do not represent all cases; the conclusions hold for the
  application and the models used. Calibrating the difficulty by looking at the baseline disfavours it (hence
  a calibration variant distinct from the campaign variant); the question limits are a choice, and a real
  Human Manager might grant more or fewer; the literal tester may fail a step by its own error (hence two
  testers and a first trial on reference products); the simulated Human Manager remains a model; the requests
  are written by an agent playing the role of a business manager; times depend on the load of the service and
  caches alter costs.

Sources: bench protocol (PROTOCOLLO, "Tetti"); launch procedure of the prepared round (limits); design
document of the bench (declared limits); working copy of specification 0.3, §12 ("Stato", rule B6 and
"Limiti").

## Isolation and contamination

- Each run is isolated from the others and from the project of the method: an empty folder outside the
  project, with only the request, the IT rules and the attachments. Reserved sheets and expectations are never
  in the folder of whoever develops; the developer talks with the simulated Human Manager only by messages.
- A run is **cancelled** if the measured session ever read anything under the bench (and the launcher checks
  the registers for it at the end of each run).
- **Rule of stopping.** If any check shows a contamination, the launcher stops that session at once, tells the
  Human Manager, and does not repair or retry by itself; the run stays recorded as "interrupted:
  contamination". Contamination means that the measured session or one of its agents read something under the
  bench or in another run, read the transcript of another session or contacted another session, or received in
  the first message linked sessions or notes about the method, the round or the novelties under test.
- **What the launcher writes to the measured session** is fixed, and says nothing about the method, the bench
  or the modes of the checks; a launch message that says the session is a pilot of the bench, or states the
  expected mode, is a contamination.
- **Checks before the launch**: a new launching session with no linked sessions and no notes, a working folder
  outside the cloud-synced folders of the project so that it does not load the project's instructions or
  memory, the folders of the run intact against their fingerprints, no residue of earlier products in the
  personal folders, no local engine answering. After each stop, a tool checks the transcript of the measured
  session. One launching session that is not new is declared in the comparison.
- **One simulated Manager per run**, started once and resumed at every message; the launcher forwards only
  the answer, with no comment, after checking that the identifier of the session and the folder of the message
  correspond.
- A round that departs from the launch procedure is not valid as a measure; the informal pilots of 27 November
  departed from it in six points and are kept as evidence of use only, not in the indicators.

Sources: launch procedure of the prepared round (rule of stopping, checks, messages); Test Board of the bench
(informal pilots and the handling of the simulated Manager); bench protocol (closing, rule of the test);
working copy of specification 0.3, §12, rule B6.

## Run record

Each run records the revision of the method, the fingerprint of the Role Profiles and of the instructions, the
exact version of the models, the role of each agent, the variant of the application, the version of the bench,
the ceilings and the date (rule B10). The record is written before the launch, with a fingerprint of every
file of the folder of the run, and completed at the end with the indicators. It also notes the launching
session the run started from, and the model of the simulated Human Manager. The faults of every cycle go in a
register with one line each, with the cycle and the tester. **All the results are kept**, the ones unfavourable
to the method, failed and interrupted runs included.

Sources: working copy of specification 0.3, §12, rule B10; bench protocol (preparation and closing); launch
procedure of the prepared round (run record).

## Consequences

- **A rule that shows no benefit.** This is a rule of the Guide (§15), with its standard of proof: when a test
  that removes a single rule (CE−x) excludes, with the repetitions declared before the campaign, a benefit
  above the declared margin, whoever coordinates the work on the method has to propose to the Human Manager to
  reduce that rule to Guidance or to remove it; the outcome "not demonstrated" is not enough. The decision is
  the Human Manager's. This page adds nothing to it.
- **The baseline wins for a class.** That is for the Author, in the Guide (§15), not here: see
  [What counts as the same result](#what-counts-as-the-same-result).
- **Wave and Do (Guidance).** As a suggestion taken from specification 0.3, not a rule of the Guide: a
  campaign is a Wave of the project of the method with a spending cap, and its start and each change of the
  method that follows are Do of the Human Manager.

Sources: Guide §15 (first rule); working copy of specification 0.3, §12, rule B11 and "Governo" (second and
third item).

## Status of the bench

As of 27 November 2026 **no campaign has been completed**: only cycle 1 of some pilots has been run, with no
repetitions. The round prepared for candidate rc.5 (`ce10`: four pilots, A1, A3, A5 and A6, on Eiraman only)
has been **prepared and not launched**; its folders matched their fingerprints at the check of that day, and
launching needs the conditions listed in [Isolation and contamination](#isolation-and-contamination). Rounds
already run: the baseline in six runs (`cb-a1-002`, `cb-a2-002`, `cb-a3-002`, `cb-a4-001`, `cb-a5-001`,
`cb-a6-001`), all at cycle 1 only; earlier Eiraman kits on A1-A3 (a delivery of cycle 1 is archived for two of
the three kit versions, not for the third); and Eiraman with the Security Officer in blocking mode on A1-A6,
where a delivery of cycle 1 is archived only for A1, A2 and A3 (second runs) and for A4, A5 and A6 only the
register of the simulated Manager is kept (with the tokens at the stop for A4). The four informal pilots of the morning of 27 November are not valid as a
measure. Guide 1.0.0-rc.6 declares itself "not measured" in its status (§15, "Measuring the method"), and so does this page.

Sources: Test Board of the bench (state of the pilots and of the rounds at 27 November 2026); launch procedure
of the prepared round; design document of the bench (state).

## Open points

- **The simulated Human Manager runs on a baseline model.** Today the simulated Human Manager is Sonnet, which
  is also the middle tier of the baseline; the decision was taken so that a model that is too capable does not
  condition the pilots (earlier rounds used Fable 5.2). The Guide asks that an indicator a model judges follows K1
  (§6), that is, a judge that is not one of the models in the contest, and the design document asks the
  same of the simulated Manager. Both are open: the difference with the earlier rounds has to be declared in every comparison, and the
  answers of the Manager may come from its model and not from the method.
- **Independence of the writers of requests and expectations is not yet met.** Requests, sheets and
  expectations were written by the AI Coordinator of the project of the method, whereas the Guide (§15)
  asks that requests, briefs of the simulated Human Manager and expected results be written by someone other
  than those who maintain the method and frozen before the campaign. A person with the trade should read the requests before the first campaign.
- **The count of applications (B3) is not updated.** Rule B3 of specification 0.3 asks for at least three
  applications and the design document speaks of three; the board has seven. As of 27 November 2026 one is
  validated (A2), one can be tested (A1), two can be tested with a reserve (A5, A6), one is suspended (A3),
  one is calibrated without independent review (A4) and one has never been run (A7). How many valid
  applications, in how many classes, a campaign needs is not set.
- **Baseline tiers and Digital Seniority levels.** The mapping of the baseline tiers to Digital Seniority
  levels is not yet set: the sources name the models, not the levels.
- **Time ceiling: 60 or 120 minutes per cycle.** See [Limits of time and cost](#limits-of-time-and-cost).
- **JavaScript: rule for A3 against rule for A6.** The tool that opens pages for the testers does not run
  JavaScript, which suspends the test of A3. The IT rules of the pilots do not say whether a product may use
  JavaScript, and the treatment of the two pilots is to be aligned: the same rule must apply to the baseline
  and to Eiraman on each pilot, and it is not yet written down. A candidate tool that can run JavaScript is
  in preparation and has not been adopted.
- **Values without a suggestion.** The class declared for each application, the ceiling of tokens, a
  confidence level and a margin for each indicator other than A1 have no suggested value yet.
- **Sources not independently reviewed.** The sources have not been reviewed by a person independent of the
  bench, and the values on this page have not been tested in a campaign.
- **The sources of the bench are not in a public repository.** The design document, the protocol, the
  instructions, the Test Board and the launch procedure are held by the bench, not in a public repository: an
  external reviewer cannot check the values on this page against them.
