# Language Model Uncertainty Quantification with Attention Chain  
**Authors:** Li et al.  
**Year:** 2025  

---

## Core Idea
This paper introduces **Attention Chain Uncertainty Quantification (AC-UQ)**, a method to estimate model confidence by focusing only on the *essential reasoning steps* within a long chain-of-thought (CoT).  
Instead of treating the entire reasoning sequence as a joint probability (which includes many auxiliary or redundant tokens), AC-UQ extracts a condensed sequence of *attention-critical tokens* — denoted as $x_{\text{attn}}$ — and uses it to calculate the conditional probability of the final answer.

---

## Motivation
- **Problem with joint probability:**  
  Directly using $P_{\mathcal{M}}(x_{\text{ans}}, x_{\text{cot}} \mid x_{\text{instr}})$ is biased because the CoT sequence includes filler tokens with little semantic value, making probabilities small and unintuitive.  
- **Insight:**  
  Confidence in the **final answer** should not depend heavily on irrelevant reasoning tokens.  
- **Goal:**  
  Construct a compact approximation that reflects true answer confidence while avoiding exponential computation over all possible reasoning sequences.  

---

## Key Equations

1. **Joint formulation (intractable):**

   ![equation1](https://latex.codecogs.com/svg.latex?P_%7B%5Cmathcal%7BM%7D%7D%28x_%7B%5Ctext%7Bans%7D%7D%20%5Cmid%20x_%7B%5Ctext%7Binstr%7D%7D%29%20%3D%20%5Csum_%7Bx_%7B%5Ctext%7Bcot%7D%7D%7D%20P_%7B%5Cmathcal%7BM%7D%7D%28x_%7B%5Ctext%7Bans%7D%7D%20%5Cmid%20x_%7B%5Ctext%7Bcot%7D%7D%2C%20x_%7B%5Ctext%7Binstr%7D%7D%29%20P_%7B%5Cmathcal%7BM%7D%7D%28x_%7B%5Ctext%7Bcot%7D%7D%20%5Cmid%20x_%7B%5Ctext%7Binstr%7D%7D%29)

   where $x_{\text{cot}}$ spans all possible reasoning sequences (combinatorially huge).

2. **Approximation with attention chain**

![equation2](https://latex.codecogs.com/svg.latex?%5Ctilde%7BP%7D_%7B%5Cmathcal%7BM%7D%7D%28x_%7B%5Ctext%7Bans%7D%7D%5Cmid%20x_%7B%5Ctext%7Binstr%7D%7D%29%20%5Capprox%20%5Csum_%7Bx_%7B%5Ctext%7Battn%7D%7D%5E%7B%5Cprime%7D%20%5Cin%20S%7D%20P_%7B%5Cmathcal%7BM%7D%7D%28x_%7B%5Ctext%7Bans%7D%7D%2C%20x_%7B%5Ctext%7Battn%7D%7D%5E%7B%5Cprime%7D%20%5Cmid%20x_%7B%5Ctext%7Binstr%7D%7D%29)

where $x_{\text{attn}}^{\prime}\\in S$ is one distilled attention-chain; $S$ is a manageable subset.



---

## Method
1. Generate full chain-of-thought reasoning.  
2. Use attention weights to identify **salient tokens** that strongly influence the final answer.  
3. Form an **attention chain sequence** $x_{\text{attn}}$.  
4. Compute uncertainty by evaluating the conditional probability of the answer given $x_{\text{attn}}$.  

---

## Contribution
- Proposes a **more faithful and interpretable** UQ method for LLMs.  
- Reduces the bias caused by filler tokens in long CoT reasoning.  
- Provides a practical approximation to otherwise intractable joint probability computations.  
  


