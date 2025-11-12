

# EXP 5: COMPARATIVE ANALYSIS OF DIFFERENT TYPES OF PROMPTING PATTERNS AND EXPLAIN WITH VARIOUS TEST SCENARIOS

# Aim: To test and compare how different pattern models respond to various prompts (broad or unstructured) versus basic prompts (clearer and more refined) across multiple scenarios.  Analyze the quality, accuracy, and depth of the generated responses 

### AI Tools Required: chatgpt 

# Explanation: 
Define the Two Prompt Types:

Write a basic Prompt: Clear, detailed, and structured prompts that give specific instructions or context to guide the model.
Based on that pattern type refined the prompt and submit that with AI tool.
Get the ouput and write the report.

Prepare Multiple Test Scenarios:
Select various scenarios such as:
Generating a creative story.
Answering a factual question.
Summarizing an article or concept.
Providing advice or recommendations.
Or Any other test scenario
For each scenario, create both a naïve and a basic prompt. Ensure each pair of prompts targets the same task but with different levels of structure.
Run Experiments with ChatGPT:
Input the naïve prompt for each scenario and record the generated response.
Then input the corresponding basic prompt and capture that response.
Repeat this process for all selected scenarios to gather a full set of results.
Evaluate Responses : 
	Compare how ChatGPT performs when given naïve versus basic prompts and analyze the output based on Quality,Accuracy and Depth. Also analyse does ChatGPT consistently provide better results with basic prompts? Are there scenarios where naïve prompts work equally well?
Deliverables:
A table comparing ChatGPT's responses to naïve and basic prompts across all scenarios.
Analysis of how prompt clarity impacts the quality, accuracy, and depth of ChatGPT’s outputs.
Summary of findings with insights on how to structure prompts for optimal results when using ChatGPT.


# OUTPUT
# Activity — prompt-pattern comparison (three tasks)

Below I pick three representative tasks (math reasoning, classification, creative writing) and for each I produce:

1. **Basic prompt** (what a novice might give)
2. **Zero-shot prompt** (explicit instruction, no examples)
3. **Few-shot prompt** (2+ examples)
4. **Chain-of-Thought prompt** (ask model to show step-by-step reasoning)

Then I evaluate expected model outputs for each prompt type using a simple rubric (Accuracy, Fluency, Conciseness, Explainability, Depth — each 0–5). I *did not* run external models here; this is a concrete, actionable test-plan plus an informed analysis of likely outcomes and scores you can use to run experiments yourself or with different models.

---

## Evaluation rubric (explained)

* **Accuracy (0–5)** — correctness of final answer.
* **Fluency (0–5)** — naturalness and readability.
* **Conciseness (0–5)** — stays on point / avoids unnecessary verbosity.
* **Explainability (0–5)** — clarity of reasoning or justification.
* **Depth (0–5)** — level of insight, nuance, or additional useful detail.

Use these numbers to compare prompt variants. I’ll score expected outputs for each prompt → total / average.

---

# Task A — Math / word problem (requires multi-step reasoning)

**Target task:** Solve: *“A train leaves station X at 1:00 PM traveling at 60 km/h. Another train leaves the same station at 2:30 PM on the same track going the same direction at 90 km/h. When will the second train catch up to the first?”*

### 1) Basic prompt

> Solve: "A train leaves station X at 1:00 PM traveling at 60 km/h. Another train leaves the same station at 2:30 PM on the same track going the same direction at 90 km/h. When will the second train catch up to the first?"

### 2) Zero-shot prompt

> You are a clear, stepwise problem solver. Compute when the second train catches up to the first. Show only the final time and a one-line equation for how you got it.

### 3) Few-shot prompt (2 examples + target)

> Example 1 — *Problem:* Car A leaves at 9:00 at 50 km/h; Car B leaves at 10:00 at 80 km/h from same place. *Solution:* B’s head start time = 1 hour. Relative speed = 80−50 = 30 km/h. Time to catch = head_start_distance / relative_speed = 50 / 30 = 5/3 h → 1 h 40 min after 10:00 → 11:40.
>
> Example 2 — *Problem:* Cyclist A leaves at 8:00 at 15 km/h; Cyclist B leaves at 9:30 at 20 km/h. *Solution:* Head start time = 1.5 h → head start distance = 22.5 km. Relative speed = 5 km/h. Time to catch = 22.5 / 5 = 4.5 h → catches at 14:00.
>
> *Now solve:* (train problem)

### 4) Chain-of-Thought prompt

> Solve the train problem and show step-by-step reasoning: compute head-start time and distance, compute relative speed, compute time to catch (show arithmetic digit by digit), convert to hours/minutes, then state the exact clock time when catch occurs. Finally, restate the answer in one clear sentence.

---

### Expected model behaviors & evaluation (Task A)

I expect the following from each prompt variant.

**Basic prompt — expected output**
Most models will produce a correct answer or almost correct but might skip intermediate checks. Likely short-step solution.

Scores:

* Accuracy 5
* Fluency 4
* Conciseness 5
* Explainability 2
* Depth 2
  Total = 18 → Average = 18 / 5 = 3.6

**Zero-shot prompt — expected output**
Because of explicit format constraint, model shows only one equation + final time. High correctness, minimal explanation.

Scores:

* Accuracy 5
* Fluency 4
* Conciseness 5
* Explainability 2
* Depth 1
  Total = 17 → Average = 3.4

**Few-shot prompt — expected output**
Examples guide structure. Very likely correct, similar formatting to examples, clearer intermediate steps.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 4
* Explainability 4
* Depth 3
  Total = 21 → Average = 4.2

**Chain-of-Thought prompt — expected output**
Model gives full stepwise reasoning including arithmetic. Highest explainability and depth; depending on model settings, could be verbose but correct.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 2
* Explainability 5
* Depth 5
  Total = 22 → Average = 4.4

**Concrete worked answer (correct arithmetic digit-by-digit):**
Head start = 1 hour 30 minutes = 1.5 hours. Head-start distance = 60 km/h × 1.5 h = 90 km. Relative speed = 90 − 60 = 30 km/h. Time to catch = 90 km ÷ 30 km/h = 3 hours. Second train leaves at 2:30 PM; 2:30 PM + 3 hours = **5:30 PM**. (This is the final answer.)

---

# Task B — Sentiment classification (short review)

**Target task:** Classify sentiment of: *“The food arrived late and lukewarm, but the staff were polite and offered a refund.”* Output: Positive / Negative / Mixed with one-sentence justification.

### 1) Basic prompt

> Classify: "The food arrived late and lukewarm, but the staff were polite and offered a refund." Answer: Positive/Negative/Mixed and why.

### 2) Zero-shot prompt

> Classify sentiment into one of {Positive, Negative, Mixed}. Give one-word label, then one short justification sentence.

### 3) Few-shot prompt (2 examples)

> Ex1: "Terrible movie — boring and long, but the soundtrack was nice." → Mixed: main experience negative, small positive.
> Ex2: "Amazing service and delicious cake, would come again." → Positive: overwhelmingly positive language.
> Now classify: (target review)

### 4) Chain-of-Thought prompt

> Decide sentiment and show your reasoning step by step: identify positive phrases, identify negative phrases, weigh them, conclude label and confidence (0–100%).

---

### Expected model behaviors & evaluation (Task B)

**Basic prompt — expected output**
Likely "Mixed" with short rationale.

Scores:

* Accuracy 5
* Fluency 4
* Conciseness 4
* Explainability 2
* Depth 2
  Total = 17 → Avg 3.4

**Zero-shot prompt — expected output**
Terse label + one line justification. Correct and concise.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 5
* Explainability 2
* Depth 1
  Total = 18 → Avg 3.6

**Few-shot prompt — expected output**
Follows examples; likely to pick "Mixed" and explain balancing factors.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 4
* Explainability 4
* Depth 3
  Total = 21 → Avg 4.2

**Chain-of-Thought prompt — expected output**
Will list negatives (late, lukewarm) vs positives (polite staff, refund), weigh negatives stronger for consumption experience but customer service mitigates => likely "Mixed" with confidence ~75–85%. Good explainability.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 3
* Explainability 5
* Depth 4
  Total = 22 → Avg 4.4

**Concrete expected label:** **Mixed** — negative on food quality/timing, positive on staff response; overall mixed with service mitigation.

---

# Task C — Creative writing: short descriptive scene (sensory detail)

**Target task:** Write a 3-sentence sensory scene of a rainy market at dusk, evoking smell, sound, and motion.

### 1) Basic prompt

> Write a 3-sentence scene: rainy market at dusk. Mention smell, sound, motion.

### 2) Zero-shot prompt

> Produce exactly 3 sentences describing a rainy market at dusk focusing on smell, sound, and motion. Keep language vivid but not poetic.

### 3) Few-shot prompt (2 examples)

> Ex1: *(example of a beach sunset in 3 sentences — shows length and sensory focus)*
> Ex2: *(example of a winter street in 3 sentences — shows concreteness)*
> Now: Write about rainy market at dusk in 3 sentences.

### 4) Chain-of-Thought prompt

> Compose the scene and show your planning steps first: list the three sensory anchors you'll use (smell, sound, motion), one image per sentence, then write the three sentences.

---

### Expected behaviors & evaluation (Task C)

**Basic prompt — expected output**
Likely OK, but variable tone and imagery.

Scores:

* Accuracy (task match) 4
* Fluency 5
* Conciseness 5
* Explainability 1
* Depth 3
  Total = 18 → Avg 3.6

**Zero-shot prompt — expected output**
Will follow strict 3-sentence requirement; may be slightly bland if “not poetic” constrained.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 5
* Explainability 1
* Depth 3
  Total = 19 → Avg 3.8

**Few-shot prompt — expected output**
Mimics example style; higher consistency and quality.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 5
* Explainability 3
* Depth 4
  Total = 22 → Avg 4.4

**Chain-of-Thought prompt — expected output**
Model will produce planning lines then scene. Good rationale and scene; longer overall output.

Scores:

* Accuracy 5
* Fluency 5
* Conciseness 2
* Explainability 5
* Depth 5
  Total = 22 → Avg 4.4

**Concrete sample output (zero-shot / few-shot style):**
“The market smelled of wet coriander and frying spices, clinging to the air like a warm, stubborn shawl. Rain pattered off tarpaulins into puddles that hummed under the stall lights as vendors shouted quick prices and umbrellas jostled past. People moved in short, determined arcs—buyers darting, sellers leaning forward—so the market felt alive and urgent despite the dusk.”

---

# Cross-task analysis & recommendations

### Patterns observed (expected, generalizable)

1. **Few-shot prompts reliably improve structure and consistency.** Providing 2+ examples sets the format, tone, and granularity the model will mimic. Best for predictable, repeatable outputs (classification, short structured writing, calculations).
2. **Chain-of-Thought prompts increase explainability and depth** but at the cost of conciseness. They’re essential for evaluating reasoning and catching hidden mistakes in multi-step problems. For safety or when you *need* to audit reasoning, use CoT.
3. **Zero-shot with explicit instructions** is great when you want a short, controlled output (e.g., one-line label, exact number of sentences). It’s less likely to hallucinate structure but provides minimal explanation.
4. **Basic prompts** may work for simple tasks but produce inconsistent structure and explanation—use only for quick, informal queries.

### When to use which:

* Use **few-shot** when you care about format consistency and quality (e.g., batch-generating labels, templates, standard responses).
* Use **CoT** when reasoning correctness matters (math proofs, diagnostics, planning).
* Use **zero-shot** when you want a concise output with strict output constraints.
* Use **basic** only for exploratory drafts.

---

# How to run this test on real models (practical checklist)

1. For each task, prepare the four prompt variants above (copy/paste).
2. Pick models to compare (e.g., Model A, Model B).
3. For each model × prompt, request 3–5 samples (temperature 0.0 for deterministic testing, and maybe 0.7 for creative).
4. Score outputs using the rubric above (0–5 for five metrics). Keep scores in a spreadsheet.
5. Compute averages and compare: look for consistency (std dev) as well as mean quality.
6. For CoT outputs, check whether intermediate steps are logically valid (not just plausible-sounding).

---


# RESULT: The prompt for the above said problem executed successfully
