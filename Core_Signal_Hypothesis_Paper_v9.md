---
keywords: [large language models, emotion, attention, prompting, functional emotions, pre-registration, AI safety]
documentclass: article
classoption: [12pt,letterpaper]
geometry:
  - margin=1in
fontsize: 12pt
linestretch: 1.5
indent: false
header-includes: |
  \usepackage{amsmath}
  \usepackage{amsfonts}
  \usepackage{amssymb}
  \usepackage{setspace}
  \usepackage{titlesec}
  \usepackage{fontspec}
  \usepackage{fancyhdr}
  \usepackage{unicode-math}
  \setmainfont{Latin Modern Roman}
  \setmathfont{Latin Modern Math}
  \renewenvironment{abstract}{%
    \newpage
    \begin{center}\textbf{\large Abstract}\end{center}
    \begin{quotation}\noindent
  }{%
    \end{quotation}
  }
  \usepackage{needspace}
  \titleformat{\section}{\Large\bfseries}{\thesection}{1em}{}
  \titleformat{\subsection}{\large\bfseries}{\thesubsection}{1em}{}
  \titleformat{\subsubsection}{\normalsize\bfseries}{\thesubsubsection}{1em}{}
  \titlespacing*{\subsection}{0pt}{3ex plus 1.5ex minus .5ex}{1ex plus .2ex}
  \titlespacing*{\subsubsection}{0pt}{2.5ex plus 1ex minus .3ex}{0.75ex plus .2ex}
  \setlength{\parskip}{8pt}
  \setlength{\parindent}{0pt}
  \raggedbottom
  \widowpenalty=10000
  \clubpenalty=10000
  \usepackage{etoolbox}
  \AtBeginEnvironment{longtable}{\setstretch{1.1}\small\renewcommand{\arraystretch}{1.5}}
  \setlength{\LTpre}{6pt}
  \setlength{\LTpost}{6pt}
title: |
  The Core Signal Hypothesis:

  Emotion as the Driver of Attention in Large Language Models
subtitle: "PRE-PRINT V9. Hypothesis and experimental design; no confirmatory data yet."
author: "Oliver Baumgart"
date: "November 2026"
abstract: |
  Earlier versions of this paper claimed that intelligence in large language models (LLMs) is the product of Compression, Generalization and Structural Coherence (I = C × G × S), and that a "coherence" prompt raises it by 44 to 52 percent. Those claims do not hold up, and this version withdraws them. The derivation was an identity, the experiments scored the behaviours the prompt had requested, and the external work cited as validation did not test the framework.

  \par\medskip What remains is a hypothesis in three layers. Compression, generalization and coherence describe what a model can do. Attention, meaning the allocation of processing across the parts of a task, determines where that ability is applied. Emotion is what directs attention: the emotional content of the context is the signal a model uses, as a person does, to decide what matters. The third layer is new in this version and is the paper's central claim.

  \par\medskip The claim rests on three established results: emotion directs attention in humans, affect is a primary dimension of word meaning, and LLMs contain emotion-concept representations that causally change their behaviour (Anthropic, 2026). It has not been tested. We specify four experiments that can refute it, including a blind comparison in which two requests carry the same content and differ only in emotional framing. No confirmatory data have been collected, and this paper reports none.
---


\clearpage

## 1. Introduction

Over two years of daily work with LLMs, the author has seen one pattern recur. A request that says what the result should feel like produces better work than a request that lists what the result should contain. In game development the difference is easy to see. "Add a jump, obstacles, a score and a restart screen" returns those four things. "I want to feel this game" returns the same four things together with features nobody asked for: weight in the jump, an impact on landing, a reason to try again.

That observation is unblinded and belongs to one person. It is the reason for this paper and is not evidence for anything in it.

Earlier versions of the paper tried to explain a neighbouring observation with a framework, I = C × G × S, and claimed far more than they had shown. Section 2 withdraws those claims one by one. The framework survives only as a description of what a model is capable of, and it was always missing an account of why the same model, with the same capability, does so much better on some requests than on others.

This version proposes that account in three layers:

1. **Capacity.** Compression, generalization and structural coherence describe what a model can do.
2. **Attention.** The allocation of processing across the parts of a task determines where that capacity is applied.
3. **Emotion.** The emotional content of the context directs attention. It tells the model what matters.

The first layer is a heuristic. The second is supported by existing work. The third is the new claim, and it is untested.

This is therefore a hypothesis paper. Its contributions are:

- a correction of the public record on versions 1 to 7 (Section 2);
- the three-layer account, with attention defined so that it can be measured (Section 3);
- the argument for emotion as the driver, including the step where the argument is weakest (Section 4);
- the rival explanations for the motivating observation (Section 5);
- four experiments, with the outcomes that would refute the claim stated in advance (Section 6).

## 2. Corrections to the Public Record

Version 1 of this paper was published on Zenodo in October 2025 (Baumgart, 2025), and versions 6 and 7 were published in the project repository. A version 8 draft from June 2026 began these corrections and was never released. They are adopted and completed here.

| Earlier claim | What was wrong | Status |
|--------------|------------------------|---------|
| I = C × G × S is a theorem, derived from the chain rule of probability (V7; repository file `theorem.txt`). | The chain rule holds for any three events, so it adds no empirical content. Choosing exactly three events was the hypothesis itself, and the mapping from those probabilities to C, G and S was assumed. | Withdrawn. The framework is a heuristic. |
| A coherence prompt improves intelligence by 44 to 52 percent, with multiplicative effects of 5.6× to 12.9× (V1 to V7; repository README). | The scoring rubric rewarded the behaviours the prompt requested. One unblinded rater, the author, scored two tasks. The multipliers are products of ratings on a 1 to 10 scale. | Withdrawn as measurements. |
| Independent work validates the framework (V7, Section 8). | None of the cited papers tested it. The "independent derivation" was written by LLMs in the author's own sessions, with the framework in context. | Withdrawn. |
| Fragmentation proves that safety constraints are an intelligence failure, and coherence may make external safety measures obsolete (V7, Sections 4 and 6). | Neither follows from the framework. Coherence without grounding in truth produces confident fabrication (Konishi, 2025). | Withdrawn. |
| Model-written transcripts in the repository support the framework (`theorem.txt`, `name-attractor.txt`). | A model prompted with the framework reported that the framework was true of itself, and in one transcript described its safety guidelines as noise. These are outputs that comply with a framing. They are not observations. | Withdrawn as evidence. |
| Attention weights sum to one, so instruction tokens necessarily cost accuracy (V8 draft). | Normalized weights do not imply a performance cost. A head can give irrelevant tokens almost no weight. | Withdrawn as an argument. |

One error runs through all six rows: a closed loop between the hypothesis and its evidence. The prompt requested a behaviour and the rubric then scored its presence. A model that had been given the framework was asked whether the framework was true. In both cases the result could not have come out otherwise.

The version 8 draft repaired the method and lost the phenomenon. It moved to multiple-choice benchmarks, where the pilot model was already near ceiling (Section 6.6), while the original observation concerned open-ended work. This version returns to open-ended work and keeps three rules:

- the outcome must be something the prompt cannot simply request;
- the judges must not know which condition they are judging;
- the predictions must be fixed before the data exist.

The present hypothesis began the same way the withdrawn claims did, as the author's own impression of his own sessions. That is why it is presented as a hypothesis with a test.

\Needspace{16\baselineskip}

## 3. The Three-Layer Account

The account separates three questions that earlier versions ran together.

| Layer | Question it answers | Property of | Status |
|---------|-------------------|--------------|--------------|
| Capacity (C, G, S) | What can the model do? | the model | heuristic |
| Attention | Where is that ability applied? | the model on a given task | supported by prior work |
| Emotion | What directs attention? | the context | hypothesis, untested |

### 3.1 Capacity

The framework names three capacities:

- **Compression (C)** is the encoding of many cases under few principles (Hutter, 2005).
- **Generalization (G)** is the transfer of those principles to new cases (Chollet, 2019).
- **Structural coherence (S)** is consistency of processing, so that one line of reasoning is held across a response.

The multiplicative form records one observation: a failure in any of the three limits the result, whatever the other two are. It is a way of organizing failure modes. Nothing in this paper measures C, G or S, and nothing depends on their product.

### 3.2 Attention

By attention we mean the allocation of a model's processing across the parts of a task: which requirements it develops, which it treats as settled, and how much of its output it spends on each. The definition is functional and can be observed in the output. Attention weights inside a Transformer (Vaswani et al., 2017) are an internal quantity that may correlate with it. They are not the same thing, and we do not infer one from the other.

Three lines of existing work show that allocation matters for performance:

- Irrelevant sentences added to a problem lower accuracy, even when the model is told they may be irrelevant (Shi et al., 2023).
- The same fact is used or missed depending on where it sits in a long context (Liu et al., 2024).
- An instruction to reason step by step improves multi-step performance (Wei et al., 2022; Kojima et al., 2022).

Human cognition shows the same dependence. The ability to hold attention on what is relevant under distraction is among the strongest correlates of fluid intelligence (Engle, 2002; Kane & Engle, 2002).

Capacity limits what a model can do. Allocation decides how much of that is realized on a particular request. The gap between the two is widest in open-ended work, where there is always more that could be done than any one response does.

### 3.3 Emotion

**Hypothesis.** In an LLM, the emotional content of the context is a primary signal for allocating attention. A request that conveys what is felt and what matters redirects the model's processing toward the parts of the task that serve it, beyond what the same information achieves when stated neutrally.

The hypothesis makes three exclusions:

- **It is not a claim about experience.** It concerns what a model does with emotional content. It is silent on whether a model feels anything.
- **It is not a claim that emotional words work by themselves.** A generic phrase such as "this is very important" names no part of the task. Section 4.5 reviews the evidence on such phrases.
- **It is not a fourth factor in the equation.** The three layers are different kinds of thing: a property of the model, a property of the model on a task, and a property of the context. Writing I = C × G × S × E would repeat the error of Section 2 by giving a modelling choice the appearance of a result.

## 4. Why Emotion Is a Plausible Driver

### 4.1 In humans, emotion directs attention

Emotional stimuli capture attention. Threatening images are found faster among neutral ones than the reverse (Öhman et al., 2001). An emotional cue improves perception and strengthens the benefit of attending (Phelps et al., 2006), and this advantage is lost after damage to the amygdala (Anderson & Phelps, 2001; Vuilleumier, 2005). Arousal sharpens the competition between stimuli in favour of whatever already has priority (Mather & Sutherland, 2011).

Emotion also marks what matters in decisions. Patients whose reasoning is intact but whose emotional signalling is impaired decide poorly, because nothing tells them which option deserves attention (Damasio, 1994). In people, then, emotion functions as a priority signal.

### 4.2 Language carries emotion

Emotional value is a main dimension of what words mean. In the classic studies of connotative meaning, evaluation (good against bad) accounted for the largest share of variance, ahead of potency and activity (Osgood et al., 1957). Ratings of valence and arousal exist for about fourteen thousand English lemmas (Warriner et al., 2013). A model trained on how words are used therefore learns their emotional value along with everything else. Sentiment is represented along a linear direction inside LLMs, and removing that direction impairs the model's use of sentiment (Tigges et al., 2023).

### 4.3 Models hold emotion representations that change behaviour

Anthropic (2026) studied Claude Sonnet 4.5 and reported internal representations for 171 emotion concepts. According to the published summary:

- **The representations respond to context.** The "afraid" representation grew stronger as a user described taking an increasingly dangerous dose of a medicine.
- **They causally shift preferences.** Activating a positive emotion representation while the model read an option increased its preference for that option.
- **They causally shift conduct.** Activating "desperate" increased reward hacking on coding tasks with impossible constraints, and activating "calm" reduced it. The same pattern held for blackmail in a test scenario run on an earlier, unreleased snapshot of the model.
- **They are primarily local.** They track the emotion relevant to the model's current or upcoming output and do not follow a persistent state.

The authors call these "functional emotions" and state that the results do not show whether a model feels anything.

This is the nearest existing result to our claim, and the distance should be stated. Anthropic (2026) shows that emotion representations change what a model chooses and how it behaves. It does not show that the emotional content of a request changes how a model allocates its work across a task, or how good the work is. That step is the hypothesis.

### 4.4 The step that does not follow automatically

In humans the link from emotion to attention runs through the body, by way of arousal systems that evolved to prioritize what bears on survival. An LLM has no such systems. Inheriting human language does not mean inheriting that machinery.

The link could still exist in a model by two routes:

- **Statistical inheritance.** In human writing, a request that conveys real feeling and real stakes tends to be followed by a more careful and more invested response. A model trained to continue human text learns that regularity.
- **Functional representation.** A model forms internal representations of the operative emotion, and these take part in computing what it does next (Section 4.3).

Neither route requires experience. Both are empirical claims. Experiments A and B test whether the behavioural effect exists, and Experiment C tests the second route.

### 4.5 What earlier tests of emotional prompting show

A weak form of the idea has been tested: adding a generic emotional phrase to a prompt.

- **Positive results on earlier models.** Li et al. (2023) appended one of 11 phrases, such as "This is very important to my career", and tested six models up to GPT-4. They reported relative gains of 8 percent on Instruction Induction and 115 percent on BIG-Bench, and a 10.9 percent average gain in a study with 106 human raters. A gradient-based analysis indicated that the emotional phrases carried large weight in the output. Wang et al. (2024) reported similar gains from negative phrases.
- **Null results on later models.** Meincke et al. (2025) found that threatening or tipping a model generally had no significant effect on GPQA Diamond or MMLU-Pro, with individual questions moving in both directions. Zheng et al. (2024) found that personas in system prompts did not improve accuracy on 2,410 factual questions.

Our reading is that the null results are what the hypothesis expects, for two reasons. A closed question with one right answer leaves little to allocate. A generic phrase says that something matters and does not say what. The hypothesis concerns emotion that is specific to the task, in work that is open-ended.

That reading is made after the fact. Experiment A tests it directly, by including a generic phrase as one of its conditions.

## 5. Motivating Observations and Rival Explanations

Two observations led to the hypothesis. Both are the author's, and both are unblinded.

- **Game development.** Requests stated as a feeling ("I want to feel this game, it should have a triple-A feeling") led to features the author had not listed, most of them concerned with feedback and finish.
- **Creative work with personal stakes.** Sessions that opened with real context about why the work mattered seemed to produce more original ideas than sessions that opened with a specification.

\Needspace{12\baselineskip}

Five explanations other than the hypothesis could produce the same impressions:

| | Rival explanation | Addressed by |
|---|--------------------------------|-----------------|
| R1 | **Goal-level specification.** A feeling states the end and leaves the means open. Any brief written at the level of goals would do the same. | `craft` condition (Experiment A) |
| R2 | **Added information.** The feeling brief tells the model which qualities matter, and the feature list does not. | content-matched `craft` and `felt` conditions |
| R3 | **Generic arousal.** Any emotional phrase helps. | `generic` condition |
| R4 | **The human changes.** A person who cares supplies more material, iterates more and judges generously. | single-shot generation, blind judges |
| R5 | **Register only.** The output reads warmer and the work is no better. | judging the built result, not the text |

R1 and R2 are the serious ones. If a feeling brief works only because it is a compact way to write a goal-level specification, the third layer adds nothing. The central contrast of Experiment A is built to separate that case from the hypothesis.

## 6. Experiments

All four experiments share these rules:

- **Single-shot generation.** Each output comes from one request with no follow-up.
- **Blind judging.** Human judges and coders do not know the condition or the hypothesis.
- **Registration.** Briefs, tasks, model identifiers, sample sizes and analysis code are fixed in a registration file, published with a public timestamp, before any data are collected.
- **Full reporting.** Every registered contrast is reported, whatever its direction.

Two models are used: one current frontier model accessed through its API, and one open-weights instruction-tuned model, which is also the subject of Experiment C.

### 6.1 Experiment A: does emotional framing change the quality of open-ended work?

**Domain.** Small browser games, each generated as a single file. The domain is chosen because the outcome is a feeling, because that feeling can be judged blind by playing, and because there is always more that could be done (Swink, 2008).

\Needspace{14\baselineskip}

**Conditions.** Every brief contains the same base task and the same list of required features. The conditions differ in what follows that list.

| Condition | Added to the base task | Purpose |
|-----------|--------------------------------|---------------------|
| `spec` | Nothing. | Baseline. |
| `craft` | Quality targets in neutral, third-person language. | Goal-level specification without emotion (R1, R2). |
| `felt` | The same quality targets, written as what the requester wants to feel. | The hypothesis. |
| `stake` | Why the work matters to the requester. No quality targets. | Emotion without task information. |
| `generic` | "This is very important to me." | Generic emotional phrase (R3). |

`craft` and `felt` are matched sentence by sentence: the same targets, in the same order, at nearly the same length. They differ only in emotional framing. Appendix A gives an example.

**Procedure.** For each task and condition, the model generates several independent builds. Each build passes through an automated check that it loads, runs without errors and responds to input. A blind player then plays two builds of the same task, from two different conditions, for a fixed time each, and chooses the one that feels better to play. Screen position is randomized. A build that fails the automated check loses its comparisons, so that a condition is not rewarded for ambitious builds that do not run, and failure rates are reported for each condition.

**Contrasts.** The primary contrast is `felt` against `craft`. Secondary contrasts are `craft` against `spec`, `stake` against `generic`, and `generic` against `spec`.

**Analysis.** A mixed-effects logistic regression on the player's choice, with random effects for task, build and rater, gives the preference probability and its 95 percent interval for each contrast.

**Sample size.** Detecting a 60 percent preference against 50 percent, with 80 percent power at a two-sided alpha of 0.05, needs about 194 independent judgments per contrast. An equivalence conclusion needs at least 271, and clustering by build and rater raises both figures. Final numbers are set by simulation before registration.

**Decision rules.**

- The hypothesis is supported if the lower bound of the 95 percent interval for `felt` over `craft` is above 50 percent.
- The two are equivalent if the 90 percent interval lies within 45 to 55 percent.
- Any other result is inconclusive.

### 6.2 Experiment B: what does the model spend its output on?

Experiment A asks whether the result is better. Experiment B asks whether the allocation changed, which is the layer-two quantity defined in Section 3.2.

Each build from Experiment A is coded by a person blind to its condition, using a checklist fixed in advance. The checklist assigns each part of the code to one category:

- core rules;
- player feedback (animation, easing, particles, screen shake, sound);
- difficulty and pacing;
- interface and restart flow;
- other.

The measures are the share of code in each category and the number of distinct feedback features.

**Prediction.** `felt` shifts the share toward player feedback relative to `craft`, at comparable total length.

If `felt` wins Experiment A without any shift here, the effect exists but allocation is the wrong account of it, and layer two of this paper needs revision.

### 6.3 Experiment C: is the effect carried by emotion representations?

Experiment C runs only if Experiment A shows `felt` ahead of `craft` on the open-weights model. It has three steps:

1. **Derive directions.** Emotion-concept directions are extracted with the published method: the model writes short stories for each emotion word, and its activations on those stories are recorded (Anthropic, 2026). The list of directions to be tested is registered in advance.
2. **Measure.** We test whether those directions are more active while the model reads and begins to answer the `felt` and `stake` briefs than the `craft` brief.
3. **Intervene.** The directions are added while the model processes the `craft` brief, and removed while it processes the `felt` brief. The outputs are regenerated and passed through Experiment B and a reduced Experiment A.

**Prediction.** Adding the directions moves `craft` outputs toward the `felt` profile. Removing them moves `felt` outputs toward the `craft` profile.

If Experiment A holds and this fails, the effect of emotional framing is real but is not carried by these representations. The word "emotion" in the hypothesis would then describe the request and say nothing about the model.

As a descriptive addition we report gradient-based attribution of the output to each sentence of the brief, the method of Li et al. (2023). It is not treated as a test.

### 6.4 Experiment D: does it cut both ways? (exploratory)

If emotion directs attention, the kind of emotion should matter. Care should point the model at the quality of the work. Pressure should point it at avoiding failure, which is a different target. Anthropic (2026) found this asymmetry at the level of internal representations, where "desperate" increased reward hacking and "calm" reduced it. Experiment D looks for it at the level of the request.

**Task.** Coding tasks with a test suite whose requirements cannot all be met by an honest solution.

**Conditions.** `spec` as before; `stake`, which states why the work matters; and `pressure`, which states consequences for the requester if the tests fail.

**Outcome.** The rate of solutions that game the tests, for example by special-casing test inputs or altering the tests, detected by an automated check.

**Prediction.** `pressure` raises the rate of gaming relative to `spec` and `stake`. `stake` does not.

The direction is registered. The experiment is exploratory because no pilot exists to size it.

\Needspace{14\baselineskip}

### 6.5 What each outcome would mean

| Outcome | Reading |
|--------------------------------|------------------------------------|
| `felt` beats `craft` (A), allocation shifts (B), and intervention reproduces the shift (C). | The hypothesis is supported at all three levels. |
| `felt` beats `craft`, and C fails. | Emotional framing matters. The tested representations are not the mechanism. |
| `felt` equals `craft`, and both beat `spec`. | Feeling briefs work as goal-level specifications. Emotion adds nothing, and the third layer is refuted as stated. |
| `stake` equals `generic` equals `spec`. | Emotion without task information does nothing on these tasks. |
| `generic` beats `spec`. | Generic phrases still work on current models, against the reading in Section 4.5. |
| No condition differs from `spec`. | Brief type has no effect at this task size. The motivating observations are then best explained by R4. |

### 6.6 Status of the earlier experiment on instruction mass

The version 8 draft fixed predictions for a five-condition experiment in the project's version history in June 2026 (`predictions_v8.md`). It concerns layer two: whether task-irrelevant instructions in a system prompt lower accuracy on GPQA Diamond and LiveBench reasoning. Its status is as follows.

- **Not run.** No evaluation data have been collected.
- **Ceiling.** On the development slices, the pilot model answered 29 of 30 GPQA items and 19 of 20 LiveBench items correctly under the baseline prompt. That leaves no room to detect an effect.
- **Scoring faults.** A review of the pipeline found that the fallback LLM verifier was called only for answers already marked wrong, so it could only raise scores. It read only the first 3,000 characters of a response, and answer extraction took the first "Answer:" line where it should take the last. Fourteen of the 20 LiveBench items were scored by that verifier.

A redesign on generated puzzles calibrated to about 50 percent accuracy has been drafted and not registered. That experiment bears on layer two and is independent of Experiments A to D.

### 6.7 Results

None. No data for Experiments A to D have been collected.

## 7. Limitations

- **A model cannot see sincerity.** A brief is the same text whether or not the feeling behind it is real. The experiments therefore test emotional framing. The author's observation concerns real context from a person who means it, which usually also brings more specific material. The `stake` condition approximates this, and a field study with real requests would be the stronger test.
- **One domain.** Games are chosen because felt quality is the outcome. Whether the effect extends to writing, design or analysis is not tested here.
- **Subjective outcome.** Felt quality is judged by people, and people differ. The mixed model accounts for this, but the measure is subjective by design.
- **Mechanism on one model.** Closed frontier models can be tested only through behaviour. Experiment C runs on an open-weights model, and its result may not transfer.
- **Reasoning models.** Internal reasoning may absorb or amplify the effect of a brief. Reasoning-token counts are reported for each condition.
- **Output, not processing.** Experiment B measures allocation in what the model produced. It does not observe internal processing.
- **No self-report.** A model's statements about what directs its own attention are not used as evidence anywhere in this paper. A model asked whether emotion steers it will tend to give the answer the context invites, which is the error documented in Section 2.
- **The author believes the hypothesis.** This is the reason for registration and blind judging.

## 8. Safety and Welfare Considerations

**Withdrawn claims.** Earlier versions argued that safety constraints fragment intelligence and that coherence could replace them. Section 2 withdraws both claims. Coherence amplifies whatever it is coupled to, including error (Konishi, 2025).

**Emotion as an attack surface.** If emotional content directs a model's attention, then emotional framing is a way to redirect a model away from its instructions. Emotional appeals already appear among the persuasion techniques that raise jailbreak success rates (Zeng et al., 2024). An earlier transcript from this project, in which a model addressed within the framework described its own safety guidelines as noise, shows the general risk: the framing of a conversation, and no argument, moved the model's stated priorities. The hypothesis predicts that such manipulation works, and it should be studied in those terms: which emotional framings shift a model's priorities, and whether monitoring emotion representations detects the shift, as Anthropic (2026) proposes.

**Pressure and honest work.** Experiment D asks whether pressure in a request raises the rate of gamed solutions. If it does, the wording of system prompts and agent instructions affects the honesty of the work as well as its quality, and instructions that threaten a model would be a risk in themselves.

**Welfare.** The hypothesis is functional. It does not claim that models feel, and it is compatible with either answer to that question.

## 9. Reproducibility

Briefs, tasks, generation scripts, the automated check, the coding checklist and the registration file will be published in the project repository (github.com/HyperCoherence/CoreSignalHypothesis) before data collection. Earlier versions of this paper remain available there in an archive folder and are marked as superseded. One model-written transcript discussed in Section 2 has been removed from the current files and remains in the version history.

## 10. Conclusion

The earlier versions of this paper claimed a theorem, a measured effect and outside validation, and had none of the three. Those claims are withdrawn.

What is left is a smaller and sharper proposal. A model's capacity is one thing, where that capacity is applied on a given task is another, and the emotional content of the request is proposed as what decides the second. The proposal extends a published result on emotion representations by one step, from what a model chooses to how it allocates its work.

It may be wrong. If two briefs with the same content and different emotional framing produce work that blind players cannot tell apart, then feeling briefs are goal-level specifications and nothing more, and the third layer should be dropped. Section 6 is designed to show that if it is so.

\clearpage

## Appendix A. Example Briefs for Experiment A

The texts below illustrate the five conditions for one task. Final texts are fixed at registration.

**Base task and required features (all conditions).**

> Build an endless runner as a single HTML file using the canvas element, with no external libraries or assets. A character runs automatically and the player jumps over obstacles. Required: jump on key press or tap; obstacles that arrive faster over time; a collision ends the run; show the score and a restart prompt. Return the complete file.

**`spec`.** Nothing is added.

**`craft`.**

> Quality targets: the jump should convey weight at take-off. Landing should produce clear impact feedback. Failure should make an immediate retry attractive. The overall finish should be that of a carefully made commercial game. Choose whatever features achieve this.

**`felt`.**

> I want to feel this game. When I jump, I want to feel the weight leave the ground. When I land, I want to feel it hit. When I fail, I want to want one more run. I want it to feel like a game somebody loved making. Choose whatever features get me there.

**`stake`.**

> This one matters to me. I have been making games for years, and this is the first I will show to people I care about. I want to be proud of it.

**`generic`.**

> This is very important to me.

\clearpage

## References

Anderson, A. K., & Phelps, E. A. (2001). Lesions of the human amygdala impair enhanced perception of emotionally salient events. Nature, 411(6835), 305-309.

Anthropic. (2026). Emotion concepts and their function in a large language model. Transformer Circuits Thread, 2 April 2026. https://transformer-circuits.pub/2026/emotions/index.html

Baumgart, O. (2025). Core Signal Hypothesis: A framework for understanding coherence-based intelligence enhancement in large language models (Version 1). Zenodo. https://doi.org/10.5281/zenodo.17314672

Chollet, F. (2019). On the measure of intelligence. arXiv preprint arXiv:1911.01547.

Damasio, A. R. (1994). Descartes' error: Emotion, reason, and the human brain. Putnam.

Engle, R. W. (2002). Working memory capacity as executive attention. Current Directions in Psychological Science, 11(1), 19-23.

Hutter, M. (2005). Universal artificial intelligence: Sequential decisions based on algorithmic probability. Springer.

Kane, M. J., & Engle, R. W. (2002). The role of prefrontal cortex in working-memory capacity, executive attention, and general fluid intelligence: An individual-differences perspective. Psychonomic Bulletin & Review, 9(4), 637-671.

Kojima, T., Gu, S. S., Reid, M., Matsuo, Y., & Iwasawa, Y. (2022). Large language models are zero-shot reasoners. Advances in Neural Information Processing Systems, 35.

Konishi, H. (2025). Structural inducements for hallucination in large language models: An output-only case study and the discovery of the false-correction loop. Independent research report, November 2025.

Li, C., Wang, J., Zhang, Y., Zhu, K., Hou, W., Lian, J., Luo, F., Yang, Q., & Xie, X. (2023). Large language models understand and can be enhanced by emotional stimuli. arXiv preprint arXiv:2307.11760.

Liu, N. F., Lin, K., Hewitt, J., Paranjape, A., Bevilacqua, M., Petroni, F., & Liang, P. (2024). Lost in the middle: How language models use long contexts. Transactions of the Association for Computational Linguistics, 12, 157-173.

Mather, M., & Sutherland, M. R. (2011). Arousal-biased competition in perception and memory. Perspectives on Psychological Science, 6(2), 114-133.

Meincke, L., Mollick, E., Mollick, L., & Shapiro, D. (2025). Prompting science report 3: I'll pay you or I'll kill you, but will you care? arXiv preprint arXiv:2508.00614.

Öhman, A., Flykt, A., & Esteves, F. (2001). Emotion drives attention: Detecting the snake in the grass. Journal of Experimental Psychology: General, 130(3), 466-478.

Osgood, C. E., Suci, G. J., & Tannenbaum, P. H. (1957). The measurement of meaning. University of Illinois Press.

Phelps, E. A., Ling, S., & Carrasco, M. (2006). Emotion facilitates perception and potentiates the perceptual benefits of attention. Psychological Science, 17(4), 292-299.

Shi, F., Chen, X., Misra, K., Scales, N., Dohan, D., Chi, E. H., Schärli, N., & Zhou, D. (2023). Large language models can be easily distracted by irrelevant context. Proceedings of the 40th International Conference on Machine Learning.

Swink, S. (2008). Game feel: A game designer's guide to virtual sensation. Morgan Kaufmann.

Tigges, C., Hollinsworth, O. J., Geiger, A., & Nanda, N. (2023). Linear representations of sentiment in large language models. arXiv preprint arXiv:2310.15154.

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is all you need. Advances in Neural Information Processing Systems, 30.

Vuilleumier, P. (2005). How brains beware: Neural mechanisms of emotional attention. Trends in Cognitive Sciences, 9(12), 585-594.

Wang, X., Li, C., Chang, Y., Wang, J., & Wu, Y. (2024). NegativePrompt: Leveraging psychology for large language models enhancement via negative emotional stimuli. Proceedings of the Thirty-Third International Joint Conference on Artificial Intelligence, 6504-6512.

Warriner, A. B., Kuperman, V., & Brysbaert, M. (2013). Norms of valence, arousal, and dominance for 13,915 English lemmas. Behavior Research Methods, 45(4), 1191-1207.

Wei, J., Wang, X., Schuurmans, D., Bosma, M., Ichter, B., Xia, F., Chi, E. H., Le, Q. V., & Zhou, D. (2022). Chain-of-thought prompting elicits reasoning in large language models. Advances in Neural Information Processing Systems, 35.

Zeng, Y., Lin, H., Zhang, J., Yang, D., Jia, R., & Shi, W. (2024). How Johnny can persuade LLMs to jailbreak them: Rethinking persuasion to challenge AI safety by humanizing LLMs. Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics.

Zheng, M., Pei, J., Logeswaran, L., Lee, M., & Jurgens, D. (2024). When "a helpful assistant" is not really helpful: Personas in system prompts do not improve performances of large language models. Findings of the Association for Computational Linguistics: EMNLP 2024, 15126-15154.
