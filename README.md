# Core Signal Hypothesis

**Emotion as the Driver of Attention in Large Language Models**

Oliver Baumgart | HyperCoherence Labs | Version 9, November 2026

**Status:** hypothesis and experimental design. No confirmatory data have been collected.

Paper: [PDF](Core_Signal_Hypothesis_Paper_v9.pdf) | [Markdown](Core_Signal_Hypothesis_Paper_v9.md)

## The hypothesis

Why does the same model, with the same ability, do much better on some requests than on others? Version 9 proposes an answer in three layers.

| Layer | Question it answers | Status |
|---|---|---|
| Capacity (compression, generalization, structural coherence) | What can the model do? | heuristic |
| Attention | Where is that ability applied? | supported by prior work |
| Emotion | What directs attention? | hypothesis, untested |

The third layer is the claim: the emotional content of a request is a primary signal a model uses to decide what matters in a task. It extends published work on emotion-concept representations in LLMs ([Anthropic, 2026](https://www.anthropic.com/research/emotion-concepts-function)) by one step, from what a model chooses to how it allocates its work.

The claim is functional. It says nothing about whether a model feels anything.

## What earlier versions got wrong

Versions 1 to 7 claimed more than they had shown. Version 9 withdraws these claims (Section 2 of the paper):

- **"I = C × G × S is a theorem."** The derivation was an identity applied to a chosen decomposition. The framework is a heuristic.
- **"Coherence prompting improves intelligence by 44 to 52 percent."** The rubric rewarded the behaviours the prompt requested, and one unblinded rater scored two tasks.
- **"Independent work validates the framework."** None of the cited papers tested it.
- **"Safety constraints are an intelligence failure."** This does not follow from the framework.
- **Model-written transcripts as supporting material.** They are outputs of a model that had been given the framework, and they are not evidence.

## How the hypothesis will be tested

Section 6 of the paper specifies four experiments and states in advance the outcomes that would refute the claim.

- **A. Blind quality comparison.** Two briefs carry the same content. One states it neutrally, and one states it as what the requester wants to feel. Blind players compare the resulting game builds.
- **B. Allocation.** A blind coder classifies what each build spent its code on.
- **C. Mechanism.** On an open-weights model, emotion-concept directions are added and removed to see whether they carry the effect.
- **D. Pressure (exploratory).** Whether pressure in a request raises the rate of solutions that game their tests.

If the two briefs in Experiment A produce work that blind players cannot tell apart, the third layer is refuted as stated.

The registration file, briefs and code will be published here before any data are collected.

## Repository

| Path | Contents |
|---|---|
| `Core_Signal_Hypothesis_Paper_v9.pdf`, `.md` | Current version |
| `archive/` | Versions 1, 6 and 7 with their supporting files. Superseded, and kept for the record. |

Changes made with version 9 (November 2026):

- Earlier versions and their supporting files were moved to `archive/`.
- `name-attractor.txt`, a model-written session transcript, was removed from the current files. The paper explains why it is not evidence (Section 2). It remains in the version history.
- Copies of third-party papers were removed from the repository.

## Citation

```bibtex
@misc{baumgart2026coresignal,
  title  = {The Core Signal Hypothesis: Emotion as the Driver of Attention in Large Language Models},
  author = {Baumgart, Oliver},
  year   = {2026},
  note   = {Preprint, version 9},
  url    = {https://github.com/HyperCoherence/CoreSignalHypothesis}
}
```

Version 1 is on Zenodo ([10.5281/zenodo.17314672](https://doi.org/10.5281/zenodo.17314672)) and is superseded by this version.

## Contact

**Email:** public@hypercoherence.com
**Website:** https://hypercoherence.com

## License

[CC BY 4.0](LICENSE)
