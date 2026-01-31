> running notes on the fundamentals of deep learning, MLOps, and the LLM Lifecycle

**RLHF (Reinforcement Learning from Human Feedback)**
The model learns to generate better responses by getting feedback from *real humans*. A human rater compares two model outputs and picks the better one. That preference data trains a "reward model," which then guides the AI to produce responses more humans would prefer.
*Example:* We ask an AI "How do I bake a cake?" It gives two answers. A human says, "Answer B is more helpful and accurate." The model learns from that signal to generate answers like B in the future.

**RLAIF (Reinforcement Learning from AI Feedback)**
Same concept, but instead of humans providing the feedback, *another AI* (like a larger, more capable model) acts as the judge. It scores or compares the outputs, and that signal is used to train the model.
*Example:* The same cake question goes to GPT or Claude as a judge. It evaluates both answers and picks the better one. That AI-generated preference signal then trains the smaller model. No human in the loop needed.

**Key difference:** RLHF uses *humans* as the judge; RLAIF replaces that judge with *another AI*, making it faster and more scalable, but potentially inheriting the judge model's own biases.
