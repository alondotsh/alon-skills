# alon-fact-check

`alon-fact-check` is a fact-checking and source-tracing skill for verifying factual claims from a URL or pasted text.

It extracts explicit, verifiable claims, checks them against authoritative sources, traces claims back to original or official source URLs, and returns a structured report with verdicts, credibility ratings, source links, and key qualifiers.

[简体中文](./README.zh.md)

## Quick Install

```bash
npx skills add alondotsh/alon-skills --skill alon-fact-check
```

## When to Use

Use this skill when the user wants to:

- Verify whether a factual claim is true, false, misleading, or unverified.
- Check a URL, article, post, or pasted paragraph for factual reliability.
- Compare a claim against official, primary, peer-reviewed, or professional fact-checking sources.
- Understand the narrower accurate version of an overbroad or misleading claim.
- Trace a claim, quote, number, or partner benefit back to its original or official source URL.

Do not use it for opinion editing, general research summaries, lifestyle advice, or personalized medical/legal/financial advice.

## Input Types

### URL

For URL input, the skill first reads and summarizes the source page before fact-checking it.

The final report includes:

- `Source Summary`: what the page argues or claims.
- `Summary`: what the evidence shows after verification.

This prevents external search results from contaminating claim extraction.

### Pasted Text

For long pasted text, article-like text, transcripts, or multi-paragraph input, the skill writes a `Content Summary` before extracting claims.

For short direct claims, the summary field is omitted so the report stays compact.

### Source Tracing

For source tracing requests, the skill searches for the original, official, or earliest reliable source behind a claim.

Use this when the user asks for:

- original source
- official source
- source URL
- where a number or quote came from
- `官方出处`
- `原始出处`
- `溯源`

The source trace distinguishes official sources from secondary mentions, social posts, reposts, and other propagation nodes. When useful, it includes 1-3 representative secondary URLs so the user can compare how the claim is spreading.

## Workflow

1. Parse the input as either URL or text.
2. If the user asks for source tracing, find the best original or official source and return a source trace.
3. Understand the source content when the input is a URL or long text.
4. Extract 1-5 explicit, verifiable claims.
5. Search authoritative sources, including contradiction-oriented searches for controversial claims.
6. Classify each claim as true, misleading, false, or unverified.
7. Assemble a clean final report once, with no duplicated claim sections or mismatched sources.

## Output Shape

The report is conclusion-first:

```text
Fact-Check Report

Source: ...
Source Summary / Content Summary: ...
Overall Assessment: ...
Summary: ...
Source Note: ...

Claim #1
Claim: ...
Verdict: ...
Credibility: ...
Note: ...
Sources:
- Source title [source type / why credible]
  URL
```

For non-English output, labels and wording should match the user's language consistently.

For source tracing requests, the report uses a source-chain shape:

```text
Source Trace

Claim: ...
Best Source: ... [Official original source / Official confirmation / Primary non-official source / Secondary source / Found secondary mention / Not found]
URL
Why This Source: ...
Source Chain:
- User-provided claim or source
- Found secondary mention or intermediate source [label]
  URL
- Official/original source
  URL
Trace Confidence: High / Medium / Low
Notes: ...
```

`Trace Confidence` describes the reliability of the source chain, not the claim's truthfulness. If the skill also performs fact-checking, claim truthfulness is reported separately as `Credibility`.

## Summary Quality

The top summary should be useful, not just short.

When relevant, it should include:

- Conditions and scope.
- Baseline or comparison.
- Time frame.
- Approximate magnitude.
- Mechanism.
- Exceptions that change the verdict.

Example:

```text
"Coffee raises LDL" is too broad. The more accurate claim is that unfiltered coffee, especially at several cups per day, may raise LDL because it retains more cafestol/kahweol, while paper-filtered coffee removes most of these diterpenes and has little LDL effect.
```

## Source Handling

Source labels describe source type or why the source is credible. They are not citation numbers and do not replace the claim-level credibility rating.

Each source must directly support or contradict the specific claim it is listed under.

## Files

- `SKILL.md`: Runtime instructions loaded by compatible agents.
- `.gitignore`: Ignores local runtime output and transient files.

## About Alon

These public skills come from Alon's real daily workflows.

Alon is actively exploring the future of agent skills and is open to connecting with people who want to build useful skills.

- GitHub: https://github.com/alondotsh
- ClawHub: https://clawhub.ai/u/alondotsh
- X: https://x.com/alondotsh
- WeChat Official Account: alondotsh
