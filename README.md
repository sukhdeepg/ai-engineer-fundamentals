> running notes on the fundamentals of deep learning, MLOps, and the LLM Lifecycle. This file defaults to ML fundamentals.

**Logistic Regression = Classification, Not Regression**
Despite the name, it's used for **classification** (predicting categories), not regression (predicting numbers).

**What it does:** Predicts the *probability* that something belongs to a particular class, then classifies based on that probability.

**Real example:** Email spam detection
- Input: Email features (word count of "free", "winner", sender domain, etc.)
- Logistic Regression calculates: "82% chance this is spam"
- Decision: If probability > 50%, classify as spam; otherwise, not spam

**How it works:**
1. Takes our input features and combines them linearly (like regular regression)
2. Passes that through a **sigmoid function** to squash output between 0 and 1
3. This gives us a probability: 0.82 = 82% likely to be Class 1

**Formula intuition:** 
- Linear part: w₁×(feature1) + w₂×(feature2) + ... 
- Sigmoid converts it to probability: output between 0 and 1

**Real-world applications:**
- **Medical diagnosis:** "What's the probability this patient has disease X based on symptoms?"
- **Credit scoring:** "Will this person default on a loan?"
- **Marketing:** "Will this customer click on the ad?"
- **Spam detection:** "Is this email spam?"

**Key characteristics:**
**Simple and interpretable:** We can see which features increase/decrease the probability
**Outputs probabilities:** Not just "yes/no" but "75% yes"
**Works well for binary classification:** Spam/not spam, fraud/legitimate, yes/no
**Linear decision boundary:** Can't handle complex, non-linear patterns (use neural networks or tree-based models for that)

**When to use:** 
- Binary classification problems (two classes)
- When we need probabilities, not just predictions
- When interpretability matters (understanding *why* a prediction was made)
- As a simple baseline before trying complex models

---

**Overfitting and Underfitting = Getting the Balance Wrong**
Both are about how well our model generalizes to new, unseen data.

**Underfitting = Model is Too Simple**
The model hasn't learned enough from the training data. It's like a student who didn't study and guesses randomly.
**Real example:** We're predicting house prices but only use a straight line based on square footage. Reality is more complex (location, age, condition matter), so our model performs poorly on both training data AND new houses.
**Signs:**
- Low accuracy on training data
- Low accuracy on test data
- Model is too basic to capture patterns
**Fix:** Use a more complex model, add more features, train longer.

**Overfitting = Model Memorized Instead of Learning**
The model learned the training data *too well*, including all the noise and quirks. It's like a student who memorized answers but doesn't understand concepts.
**Real example:** We build a house price predictor with 100 features and a super complex model. It perfectly predicts every house in our training set (even weird outliers), but fails miserably on new houses because it memorized specifics instead of learning general patterns.
**Signs:**
- Very high accuracy on training data
- Much lower accuracy on test data
- Big gap between training and test performance
**Fix:** Get more training data, use regularization (L1/L2), simplify the model, use dropout, early stopping.

---

**K-Means and KNN = Two Completely Different Algorithms (Despite Similar Names)**  
**K-Means = Unsupervised Clustering**  
**What it does:** Groups similar data points into K clusters automatically. No labels needed.  
**Real example:** We have 10,000 customer purchase records. Run K-Means with K=3, and it groups customers into 3 segments: "budget shoppers," "occasional buyers," and "premium customers". Without we telling it these categories exist.

**How it works:**  
1. Randomly place K "center points" (centroids)
2. Assign each data point to the nearest centroid
3. Move centroids to the average position of their assigned points
4. Repeat steps 2-3 until centroids stop moving

**When to use:** 
- Customer segmentation
- Image compression (grouping similar colors)
- Finding patterns in unlabeled data

**Key challenge:** We must choose K beforehand (how many clusters?).

**KNN (K-Nearest Neighbors) = Supervised Classification/Regression**  
**What it does:** Predicts a label by looking at the K closest labeled examples in our training data.  
**Real example:** We want to classify if an email is spam. KNN looks at the 5 most similar emails we've already labeled (based on word frequency, sender, etc.). If 4 out of 5 are spam, it predicts: spam.

**How it works:**
1. Store all training data
2. When a new point comes in, find the K nearest training examples (using distance, like Euclidean)
3. For classification: majority vote among those K neighbors
4. For regression: average of those K neighbors

**When to use:**
- Simple classification tasks (spam detection, recommendation systems)
- When we have labeled training data
- Small to medium datasets (slow on large data)

**Key challenge:** Computationally expensive. Must calculate distance to all training points for each prediction.

**Key Differences:**

| | K-Means | KNN |
|---|---|---|
| **Type** | Unsupervised (clustering) | Supervised (classification/regression) |
| **Needs labels?** | No | Yes |
| **What K means** | Number of clusters | Number of neighbors to check |
| **Goal** | Group similar data | Predict label of new data |
| **Example** | "Find 3 customer segments" | "Is this email spam based on similar emails?" |