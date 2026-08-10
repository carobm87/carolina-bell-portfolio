# OrbitFlow Intelligence Hub

## The problem

For a solo advisory practice, qualifying inbound work can become the real bottleneck. Client intakes are often vague, describe symptoms instead of causes, or mix several problems together. Saying yes to the wrong engagement is expensive because it consumes limited capacity, creates scope risk, and can pull the work away from the practice's actual strengths.

The core product question was not simply, "Can an LLM summarize an intake?" It was, "Can the system help make a disciplined engagement decision from an imperfect intake while keeping the recommendation narrow, practical, and safe?"

## What I built

I built a five-view React single-page application with intake, analysis, pipeline, clients, and toolbox views.

The intake is sent to a large language model and returned as a structured result. The interface renders that result as:

- Fit score
- Scope status
- Anchor entry point
- Proposed approach
- Quick win
- Recommended services
- Qualifying questions
- Risk flags
- Client brief

The output is designed to support a real operating decision, not just produce polished text.

## The decisions that mattered

### Make the rubric opinionated

I designed the evaluation logic to favor small, well-owned problems over vague, ambitious ones. That reflects the operating model of a focused advisory practice, where a narrow entry point is often more valuable than a broad transformation brief.

The system is also designed to notice when an offhand operational pain is the strongest practical entry point, even if the rest of the intake is broad. Vagueness limits the result only when there is no extractable anchor that can support a credible starting point.

### Treat workflow state as a product rule

Pipeline transitions are gated. The system refuses to skip a stage when required information is missing. This makes workflow state meaningful and prevents a polished AI response from creating false confidence that an engagement is ready to advance.

### Encode scope boundaries

I encoded boundaries so the model will not recommend work the practice will not take. Those limits include areas involving regulated or clinical data, where the risk profile and domain requirements fall outside the intended scope of the practice.

The point is not to make the model more creative. The point is to make its recommendations more operationally useful.

## Stack

- React with hooks
- Large language model API integration
- Persistent key-value storage, with a migration path for legacy records
- Generated plain-text client brief

## What I would do next

I would version the rubric as a testable artifact and add an evaluation set built from past intakes. That would make it possible to compare rubric changes, catch drift, and verify that the system continues to make the kinds of tradeoffs it was designed to make.

## Source

The source is private. A walkthrough of the architecture, product decisions, and design thinking is available on request.
