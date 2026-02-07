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