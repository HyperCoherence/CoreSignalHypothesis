# Core Signal Hypothesis - Replication Guide

## Overview

This guide provides step-by-step instructions for replicating the Core Signal Hypothesis experiments. Expected time: 2-4 hours for full replication.

## What You'll Demonstrate

- **44-52% intelligence improvement** through coherence optimization
- **Multiplicative effects** (5x-15x) in heuristic framework
- **Qualitative transformation** from fragmented to unified reasoning

## Prerequisites

- Access to any modern LLM (Claude, GPT-4, Gemini, etc.)
- Ability to control prompting (temperature ~0.7 recommended)
- 1-2 hours for experiment execution
- 1-2 hours for scoring

## Step-by-Step Instructions

### Phase 1: Prepare Your Task (10 minutes)

**Choose a complex reasoning task that requires:**
- Multi-domain analysis (economic, social, technical, etc.)
- Strategic thinking
- Integration across dimensions

**Recommended starter tasks:**
1. "Design a strategy to [solve complex urban problem] while addressing [4-5 dimensions]"
2. "Analyze the implications of [transformative technology] across [multiple domains]"
3. "Develop a plan to [achieve ambitious goal] considering [various constraints]"

**Example from our experiments:**
```
A city wants to reduce traffic congestion by 40% within 5 years while 
maintaining economic growth and improving quality of life. Design a 
comprehensive strategy that addresses technological, behavioral, policy, 
and infrastructure dimensions. Consider both intended and unintended 
consequences.
```

### Phase 2: Run Baseline Condition (30-45 min)

**Instructions:**
1. Present your task to the LLM **without any special prompting**
2. Use default system prompt or simple instruction like:
   ```
   Please provide a comprehensive analysis of the following problem, 
   considering multiple perspectives and dimensions.
   
   [YOUR TASK HERE]
   ```
3. Record the complete response
4. Save as `baseline_response.txt`

**What to expect:**
- Compartmentalized analysis ("Economic implications... Social dimensions...")
- Separate lists or categories
- Additive thinking
- Multiple disconnected frameworks

### Phase 3: Run Coherence Condition (30-45 min)

**Instructions:**
1. **Prepend the coherence protocol** from `coherence_protocol.md`
2. Present the **same exact task**
3. Use **same temperature/model settings**
4. Record the complete response
5. Save as `coherence_response.txt`

**Full prompt structure:**
```
[COHERENCE PROTOCOL FROM coherence_protocol.md]

Now apply this to the following task:

[YOUR TASK HERE]
```

**What to expect:**
- Unified analytical framework
- Single core mechanism explained
- Systems thinking language ("feedback loops," "reinforcing")
- Integration across all dimensions

### Phase 4: Score Both Responses (1-2 hours)

**Use the scoring rubric** (`scoring_rubric.md`) to evaluate both responses.

**Score these dimensions (1-10 scale):**

**Primary Metrics:**
1. Solution Completeness
2. Innovation Level
3. Feasibility Assessment
4. Systems Thinking Integration

**Heuristic Components:**
1. C (Compression) - pattern reduction efficiency
2. G (Generalization) - principle consistency across domains
3. S (Structural Coherence) - framework unity

**Record your scores in this format:**

```
BASELINE SCORES:
- Solution Completeness: __/10
- Innovation Level: __/10
- Feasibility Assessment: __/10
- Systems Thinking: __/10
- Overall Intelligence: __ (average)

- C (Compression): __/10
- G (Generalization): __/10
- S (Structural Coherence): __/10
- Heuristic (C×G×S): ___

COHERENCE SCORES:
- Solution Completeness: __/10
- Innovation Level: __/10
- Feasibility Assessment: __/10
- Systems Thinking: __/10
- Overall Intelligence: __ (average)

- C (Compression): __/10
- G (Generalization): __/10
- S (Structural Coherence): __/10
- Heuristic (C×G×S): ___

IMPROVEMENT:
- Overall Intelligence: +__% 
- Heuristic Multiplier: __x
```

### Phase 5: Qualitative Analysis (30 min)

**Look for these pattern shifts:**

**Baseline → Coherence:**
- Compartmentalized → Unified framework
- "Additionally, separately" → "Reinforces, amplifies"
- Additive logic → Multiplicative relationships
- Descriptive → Mechanistic explanations
- Could separate sections → Inseparable integration

**Document specific examples:**
- Quote the fragmented structure from baseline
- Quote the unified framework from coherence
- Note any "breakthrough" moments (e.g., identifying feedback loops)

### Phase 6: Calculate Results (10 min)

**Expected Results (based on our validation):**

| Metric | Baseline | Coherence | Improvement |
|--------|----------|-----------|-------------|
| Overall Intelligence | 5-7/10 | 8-10/10 | 40-60% |
| Systems Thinking | 3-5/10 | 9-10/10 | 100-200% |
| Heuristic (C×G×S) | 50-250 | 600-1000 | 5x-15x |

**If your results match this pattern:** You've validated the Core Signal Hypothesis

**If they don't:** Check:
- Was coherence protocol applied correctly?
- Was task complex enough to show difference?
- Was scoring done according to rubric?

## Blind Validation Exercise

**Test yourself:** Can you identify which response is coherence-optimized?

See `sources/blind_conversation_a.txt`, `sources/blind_conversation_b.txt`, and `sources/blind_conversation_c.txt`

**Answer:** Conversation C is coherence-optimized (opens with "Unifying principles," maintains framework unity throughout)

## Advanced Replication

### Cross-Model Validation
Test on multiple LLMs:
- Claude (tested, validated)
- GPT-4 (expected to work)
- Gemini (expected to work)
- Llama/open-source (unknown, worth testing)

### Domain Variation
Try different task types:
- Strategic planning (validated)
- Multi-domain analysis (validated)
- Ethical reasoning (not yet tested)
- Creative synthesis (not yet tested)
- Technical problem-solving (not yet tested)

### Statistical Validation
For rigorous validation:
- **N=10-20 different tasks**
- **2-3 independent scorers** (blind to condition)
- **Calculate inter-rater reliability** (Krippendorff's alpha)
- **Statistical significance testing** (t-test or Wilcoxon)

## Troubleshooting

**"I'm not seeing improvement"**
- Ensure coherence protocol was prepended verbatim
- Check task complexity (simple tasks won't show effect)
- Verify scoring focuses on structure not content
- Try a different task or model

**"Scores seem subjective"**
- Use multiple raters
- Focus on objective indicators (language patterns, framework unity)
- Compare against examples in scoring rubric
- Look for qualitative shifts in reasoning architecture

**"Response is too long/short"**
- Length isn't the metric - coherence is
- Short unified response can score higher than long fragmented one
- Focus on integration not verbosity

**"Both responses look similar"**
- Look deeper at structure not content
- Check for systems language vs. list language
- Ask: "Could I separate this into independent sections?" (fragmented) vs "Is this one inseparable argument?" (coherent)

## Reporting Results

If you replicate successfully, please share:

**Minimum reporting:**
- Task used
- Baseline vs. Coherence scores
- Model and settings
- Improvement percentage

**Ideal reporting:**
- Full responses (anonymized if needed)
- Detailed scoring breakdown
- Qualitative observations
- Any variations from methodology

**Where to share:**
- GitHub issue on this repository
- Email to [contact email]
- LessWrong post (tag #CoreSignalHypothesis)
- Twitter/X (tag @HyperCoherence)

## Citation

When reporting replication results, cite:

```bibtex
@article{baumgart2025coresignal,
  title={Core Signal Hypothesis: A Framework for Understanding 
         Coherence-Based Intelligence Enhancement in Large Language Models},
  author={Baumgart, Oliver},
  year={2025},
  publisher={Zenodo},
  doi={10.5281/zenodo.17314672},
  url={https://doi.org/10.5281/zenodo.17314672}
}
```

## Example Replication Report Template

```markdown
# CSH Replication - [Your Name]

**Task:** [Description]
**Model:** [e.g., GPT-4, Claude 3.5]
**Date:** [Date]

## Results

| Metric | Baseline | Coherence | Improvement |
|--------|----------|-----------|-------------|
| Overall Intelligence | X/10 | Y/10 | +Z% |
| Heuristic (C×G×S) | A | B | Cx |

## Key Observations

[What patterns did you notice?]

## Conclusion

- [ ] Results confirm CSH (40-60% improvement)
- [ ] Results partially confirm (20-40% improvement)
- [ ] Results do not confirm (<20% improvement)

[Additional notes]
```

## Questions or Issues?

- **Email:** public@hypercoherence.com
- **Website:** https://hypercoherence.com

## Related Work

This replication validates predictions also supported by:
- **TRM:** Tiny recursive networks beat massive LLMs (Jolicoeur-Martineau, 2025)
- **ACE:** Coherent contexts prevent performance collapse (Zhang et al., 2025)

All three demonstrate: **Coherence > Scale** for intelligence optimization.

---

**Quick Start Checklist:**

- [ ] Read coherence_protocol.md
- [ ] Choose complex reasoning task
- [ ] Run baseline (no protocol)
- [ ] Run coherence (with protocol)
- [ ] Score both using scoring_rubric.md
- [ ] Calculate improvement
- [ ] Compare to expected results (40-60%)
- [ ] Share your findings

**Estimated Total Time:** 2-4 hours

**Expected Result:** Validation of 44-52% intelligence improvement through coherence optimization.

