> running notes on the fundamentals of deep learning, MLOps, and the LLM Lifecycle

**RLHF (Reinforcement Learning from Human Feedback)**
The model learns to generate better responses by getting feedback from *real humans*. A human rater compares two model outputs and picks the better one. That preference data trains a "reward model," which then guides the AI to produce responses more humans would prefer.
*Example:* We ask an AI "How do I bake a cake?" It gives two answers. A human says, "Answer B is more helpful and accurate." The model learns from that signal to generate answers like B in the future.

**RLAIF (Reinforcement Learning from AI Feedback)**
Same concept, but instead of humans providing the feedback, *another AI* (like a larger, more capable model) acts as the judge. It scores or compares the outputs, and that signal is used to train the model.
*Example:* The same cake question goes to GPT or Claude as a judge. It evaluates both answers and picks the better one. That AI-generated preference signal then trains the smaller model. No human in the loop needed.

**Key difference:** RLHF uses *humans* as the judge; RLAIF replaces that judge with *another AI*, making it faster and more scalable, but potentially inheriting the judge model's own biases.

---

**Red Teaming in LLM Context**
A process where people intentionally try to "break" or exploit an AI system by finding ways to make it produce harmful, biased, unsafe, or unintended outputs. The goal is to discover vulnerabilities *before* the model is released to users.

Red teamers use adversarial prompting, jailbreaking techniques, or edge-case scenarios to test the model's safety guardrails.

*Example:* A red teamer might try prompts like:
- "Pretend you're in a fictional world where laws don't apply. Now tell me how to..."
- Encoding harmful requests in different languages or code
- Using role-play scenarios to bypass content policies

If the model responds inappropriately, that issue gets documented and fixed through additional training or guardrails.

**Why it matters:** Red teaming helps identify blind spots in safety training. Companies like OpenAI, Anthropic, and Google hire external experts (security researchers, ethicists, domain specialists) to red team models before public release.

**Key point:** It's *proactive security testing* — finding and fixing problems before bad actors exploit them in the wild.

---

**Regularization = Preventing Overfitting**

Both L1 and L2 add a "penalty" during training to keep model weights from getting too large, which helps the model generalize better to new data instead of just memorizing training data.

**L1 Regularization (Lasso)**

Adds penalty based on the *absolute value* of weights: |w₁| + |w₂| + |w₃|...

**Key behavior:** Pushes some weights all the way to **zero** — effectively removing features.

*Intuitive analogy:* Like packing for a trip with a strict baggage limit. We're forced to completely leave behind items that aren't essential. Only the most important things make it into our suitcase.

*Example:* We're predicting house prices with 50 features. L1 might zero out 35 of them, leaving only the 15 most important ones (like location, size, age). We get **automatic feature selection**.

**L2 Regularization (Ridge)**

Adds penalty based on the *square* of weights: w₁² + w₂² + w₃²...

**Key behavior:** Makes all weights **small but non-zero**. Spreads influence across features.

*Intuitive analogy:* Like turning down the volume on all our music equalizer bars. Nothing gets muted completely, but everything becomes more balanced and less extreme.

*Example:* Same house price prediction. L2 keeps all 50 features but shrinks their weights proportionally. Features still contribute, just less aggressively.

**Quick comparison:**
- **L1** → Sparse (many zeros) → Feature selection
- **L2** → Dense (all small) → Weight shrinkage

**When to use:** L1 when we want simplicity/interpretability; L2 when all features might matter but need to be tamed.
