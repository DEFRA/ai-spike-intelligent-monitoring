# AI Intelligent Monitoring Spike - Writeup

Date: `2026-01-05` to `2026-01-09`
Status: Abandoned

## Need

Manual monitoring of real-time data streams is unscalable and prone to error. Teams are currently overwhelmed by the volume of information, ranging from fast-moving political feeds to the verification of image evidence for grants. There is a specific inability to detect sophisticated fraud at scale, such as applicants submitting stock photos or tampered images for Methane and Grant trials.

The current reactive approach forces staff to passively monitor high-volume streams, missing critical signals in the noise and diverting skilled analysts from higher-value decision-making work.

## Hypothesis

We believe that deploying AI-powered background agents for continuous monitoring will shift operational models from reactive information processing to proactive risk management, enabling teams to focus on high-value decision-making rather than routine surveillance tasks.

## What we aim to discover

- Can AI agents effectively filter noise from high-volume real-time data streams (RSS feeds, news sources) and accurately identify genuine political risks or policy shifts?
- Is it feasible to automate image evidence verification using perceptual hashing and image matching against stock photo libraries to detect fraudulent submissions at scale?
- Does the "Agentic Watchdog Framework" pattern reduce manual monitoring burden while maintaining or improving detection accuracy?
- What alert threshold and confidence levels are needed to minimize false positives while ensuring critical events are surfaced to human analysts?
- How do different LLMs perform at political sentiment analysis and context evaluation for feed monitoring?

## Assumptions

- RSS and news feed APIs provide sufficiently structured data for LLM analysis without extensive preprocessing
- Perceptual hashing techniques (pHash, SSIM) can reliably detect stock photos and image tampering with acceptable false positive/negative rates
- Google Images API or similar services are accessible and cost-effective for reverse image lookup at scale
- Political risk criteria can be defined clearly enough for LLMs to make consistent filtering decisions
- The benefits of automated monitoring outweigh the infrastructure and API costs
- Human analysts will trust and act upon AI-generated alerts if confidence scoring is transparent

## Outcomes

Validated that LLMs can automatically triage live data streams as expected, successfully filtering and categorizing real-time RSS feed content. However, the implementation revealed this to be primarily an architectural pattern rather than a novel AI capability.

### Key Findings

- gd categorize streaming feed data, demonstrating the feasibility of the watchdog pattern
- The value proposition lies primarily in system design and integration patterns rather than breakthrough AI capabilities
- Embedding-based retrieval combined with LLM analysis shows promise for token optimization, as demonstrated in the [token optimization PoC](https://github.com/DEFRA/ai-spike-token-optimisation)
- Pydantic AI proved useful for obtaining reliable schema-typed outputs, though users should remain aware that the underlying model behavior remains non-deterministic despite structured output formatting

## Shortcomings

- Not able to test the vision forensics portion due to lack of test data
- LLM Guardrails causing issues with live data