**Activation Functions = What Lets Neural Networks Learn Complex Patterns**

They decide what signal a neuron passes forward.

**1. ReLU (Rectified Linear Unit)**
**What it does:** If input is positive, pass it through. If negative, output zero.
**Real example:** We're building an image classifier. ReLU helps neurons detect features like "edge detected" (positive signal) vs "no edge" (zero).
**When to use:** Default choice for hidden layers in most deep networks (CNNs, feedforward networks).
**Why popular:** Fast to compute, helps networks train deeper without gradients disappearing.
**Downside:** Some neurons can "die" (permanently output zero) if they get large negative inputs during training.

**2. Sigmoid**
**What it does:** Takes any number and squashes it between 0 and 1.
**Real example:** Spam detection: we want a final output like "0.85 = 85% chance this email is spam."
**When to use:** Output layer for binary classification (yes/no, spam/not spam, cat/not cat).
**Why not for hidden layers:** In deep networks, gradients become extremely small during backpropagation, making learning painfully slow.

**3. Tanh**
**What it does:** Squashes input between -1 and 1.
**Real example:** Sentiment analysis in RNNs: capturing both positive sentiment (+0.8) and negative sentiment (-0.7).
**When to use:** Sometimes in recurrent networks (RNNs, LSTMs) where having negative values matters.
**Advantage over sigmoid:** Centered around zero, so outputs aren't all positive (helps with gradient flow slightly better than sigmoid).

**4. Softmax**
**What it does:** Converts multiple outputs into probabilities that add up to 100%.
**Real example:** Image classification with 3 classes:
- Raw scores: [Dog: 3.2, Cat: 1.8, Bird: 0.5]
- After softmax: [Dog: 70%, Cat: 25%, Bird: 5%]
**When to use:** Output layer for multi-class classification (choosing one option from many).

**Simple decision tree:**
- Building most neural networks? → **ReLU** in hidden layers
- Final output is yes/no? → **Sigmoid**
- Final output is one choice from multiple options? → **Softmax**
- Working with RNNs/LSTMs? → Maybe **Tanh**

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