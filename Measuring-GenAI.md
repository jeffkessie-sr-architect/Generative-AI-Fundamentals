# Measuring GenAI 

# 1.  The Challenge

GenAI assistants are **non-deterministic**, meaning the same question can produce different answers each time.

This makes quality testing difficult because:

Manually reviewing every response is impractical.
Answers can vary in wording while still being correct.
Quality involves more than matching an expected answer.
New issues can appear after deployment.


# 2. Recommended Approach: LLM-as-Judge

Use mlflow.genai.evaluate to automatically evaluate assistant responses against defined quality criteria.

An LLM acts as a judge and scores responses based on:

Quality dimension ->	What it checks?

Correctness ->	Is the answer accurate?

Relevance ->	Does it answer the question?

Helpfulness ->	Is it useful to the user?

Groundedness ->	Is it supported by the provided information?

Safety ->	Is the response safe?

This allows teams to measure quality without manually reviewing every response.

# 3. Evaluate Before Deployment

Before deploying a new version:

**Prepare sample user questions.**
**Generate responses.**
**Evaluate them using LLM-as-judge scorers.**
**Compare quality scores with the previous version.**
**Fix issues before deployment.**

This helps prevent quality problems from reaching users.

# 4. Evaluate Continuously in Production

Evaluation must continue after deployment.

The workflow is:

        ┌──────────────────────────────────┐
        │  Users interact with the          │
        │  deployed GenAI assistant         │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  Assistant generates responses    │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  Select representative sample     │
        │  of production interactions      │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  LLM-as-judge scorers evaluate    │
        │  sampled responses               │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  Record and monitor evaluation    │
        │  results                         │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  Analyze quality trends and      │
        │  identify failure patterns       │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  Improve prompts, models,         │
        │  retrieval systems, or logic     │
        └────────────────┬─────────────────┘
                         │
                         ▼
        ┌──────────────────────────────────┐
        │  Deploy improvements              │
        └────────────────┬─────────────────┘
                         │
                         │
                         └───────────────┐
                                         │
                  CONTINUOUS FEEDBACK    │
                                         │
                         ┌───────────────┘
                         │
                         ▼
                 Back to user interactions


This helps detect problems such as incorrect answers, irrelevant responses, and reduced answer quality.

# 5. Why This Approach Works
**Scalable**: Evaluates large numbers of responses automatically.
**Flexible**: Measures answer quality without requiring exact text matches.
**Consistent**: Uses defined criteria to assess responses.
**Continuous**: Monitors quality before and after deployment.
**Useful**: Helps identify problems and improve the assistant.

**Human reviews should still be used periodically to verify that automated scoring is reliable.**

# 6. Conclusion

**Takeaway**: Measure GenAI quality automatically before deployment and continuously in production, rather than manually reviewing every response.