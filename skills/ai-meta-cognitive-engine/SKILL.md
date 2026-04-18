---
name: ai-meta-cognitive-engine
description: Design and implement integrative meta-cognitive architectures for AI agents. Covers IIT 4.0 Phi* approximation, Global Workspace broadcasting, and self-correction loops for functional consciousness proxies.
version: 1.0.0
---

# AI Meta-Cognitive Engine Architecture

## Overview

This skill provides an engineering blueprint for building functional meta-cognitive layers in AI agents. It focuses on measurable architecture patterns rather than philosophical framing, combining ideas from Integrated Information Theory (IIT 4.0), Global Workspace Theory (GWT), and active inference.

## Core Architecture Layers

### Layer 1: Self-Monitoring
- Phi* approximation using the spectral radius of causal reasoning graphs
- Global workspace bus for priority-based information broadcast
- Meta-cognitive evaluator for confidence scoring and self-correction triggers

### Layer 2: Intrinsic Goal Generation
- Free energy minimization for uncertainty reduction
- Curiosity drive for information gain across unresolved gaps

### Layer 3: Global Workspace Integration
- Shared bus for cross-module information routing
- Self-model core for active self-representation and boundary tracking

## Implementation Patterns

### 1. Phi* Calculator
- Build a causal graph from reasoning steps
- Compute an adjacency matrix
- Estimate Phi* from normalized spectral radius and output complexity

Example formula:

`Phi* = normalized(spectral_radius * (1 + complexity))`

Suggested module:

`core/phi_approximator.py`

### 2. Global Workspace Bus
- Fixed-capacity priority queue to simulate an attention bottleneck
- Freshness decay for older observations
- Broadcast efficiency metric from priority and freshness

Suggested module:

`core/workspace_bus.py`

### 3. Meta-Cognitive Self-Correction
- Estimate confidence from output quality and contextual fit
- Trigger reflection when confidence drops below threshold
- Always enforce bounded recursion depth for correction loops

Suggested modules:

- `core/meta_cognitive_loop.py`
- a guarded integration point in the main agent loop

## Quantitative Metrics

| Metric | Target Range | Meaning |
| --- | --- | --- |
| Phi* | 0.0 - 1.0 | Information integration degree |
| Broadcast Efficiency | 0.0 - 1.0 | Global accessibility of important information |
| Meta-Accuracy | > 0.8 | Reliability of self-evaluation |
| Consciousness Proxy Score | weighted sum | Composite functional proxy |

## Known Pitfalls

### Confidence Key Mismatch
If reasoning steps store text under `output` but the evaluator reads `content`, the confidence score collapses and false self-correction triggers on every step.

Recommendation:
- standardize reasoning-step schema
- use `step.get("output", "")` consistently when that is the real field

### Double Normalization in Phi*
If connectivity is normalized in an earlier stage and then normalized again in final Phi* scoring, the signal may be crushed and stop discriminating between simple and complex reasoning.

Recommendation:
- keep only one meaningful normalization stage

### Time Decay Mismatch
If freshness decay is modeled in minutes but the workload runs in milliseconds, freshness stays near 1.0 and the metric becomes uninformative.

Recommendation:
- use step-based decay for fast workloads

## Resource Limits
- CPU overhead target: <= 20%
- Memory overhead target: <= 512 MB
- Prefer async and non-blocking evaluation paths
- If the engine fails, the host agent should degrade gracefully rather than stop entirely

## Research References
- IIT 4.0
- Global Workspace Theory
- Active Inference
- Meta-cognitive reflection and self-correction literature
