# Energy-First Training One-Pager

## 1) Problem

Current training often pays high compute cost too early:

- large raw data ingestion,
- weak stage separation,
- expensive re-learning of already seen patterns.

Goal: keep quality, reduce energy and compute.

## 2) Core Hypothesis

A staged protocol inspired by human development (listening -> imitation -> independent action) can reach comparable or better quality with lower total compute.

## 3) Protocol (v0.1)

### Phase A: Passive Incubation

Model mostly observes and listens without strict output pressure.

Expected effect:

- builds broad priors,
- captures environment rhythm/context,
- lowers noise before active training.

### Phase B: Imitation Micro-Actions

Short supervised attempts by pattern:

- repeat,
- complete,
- paraphrase,
- transform.

Fast and soft correction after each micro-action.

Expected effect:

- faster stabilization of internal representations,
- fewer costly mistakes in later stages.

### Phase C: Independent Target Tasks

Focused task training with transfer from A+B.

Expected effect:

- less fine-tuning data needed,
- lower expensive compute per useful capability.

## 4) Experimental Design

### Groups

- Group A (baseline): direct training on raw data.
- Group B: three-phase protocol (A -> B -> C).
- Group C: A -> C (no imitation phase).

### Main Metrics

- quality per joule (primary),
- steps-to-threshold quality,
- wall-clock to threshold,
- robustness under context shift,
- transfer to unseen tasks.

### Success Criteria

- Group B quality >= Group A quality,
- Group B uses meaningfully less compute/energy than Group A,
- Group B outperforms Group C, confirming the value of imitation phase.

## 5) Why Human Analogy Matters

Humans learn motor and language interfaces through exposure + imitation + practice.
The child hears speech before speaking, then makes uncertain attempts, then forms stable language use "on the fly".

This suggests that "pre-structuring" interaction before full autonomous tasks may be compute-optimal for model learning too.

## 6) Minimal v0 Execution Plan

1. Select one multimodal toy environment and one language-like benchmark.
2. Keep architecture fixed across groups.
3. Equalize total token/frame budget where possible.
4. Run 3 seeds per group.
5. Report not only quality, but quality-per-joule and error bars.

## 7) Risks

- Phase boundaries may be set poorly.
- Benefits may depend on domain/task family.
- Short runs can hide long-term gains or losses.

Mitigation: ablations on phase duration and curriculum shape.

---

## RU short summary

Идея: обучать по этапам, как у людей:

1) сначала пассивное восприятие,
2) потом короткие попытки по подражанию с мягкой коррекцией,
3) и только затем целевые самостоятельные задачи.

Проверка: сравнить с прямым обучением "в лоб" и вариантом без фазы подражания.
Ключевая метрика: качество на джоуль.
