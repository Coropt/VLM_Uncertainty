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
   $$
P_{\mathcal{M}}(x_{\text{ans}} \mid x_{\text{instr}}) 
= \sum_{x_{\text{cot}}} P_{\mathcal{M}}(x_{\text{ans}} \mid x_{\text{cot}}, x_{\text{instr}}) 
P_{\mathcal{M}}(x_{\text{cot}} \mid x_{\text{instr}})
$$
   where $x_{\text{cot}}$ spans all possible reasoning sequences (combinatorially huge).  

2. **Approximation with attention chain:**  
   $$
   \tilde{P}_{\mathcal{M}}(x_{\text{ans}} \mid x_{\text{instr}}) 
   \approx P_{\mathcal{M}}(x_{\text{ans}} \mid x_{\text{attn}}, x_{\text{instr}})
   $$
   where $x_{\text{attn}}$ is a distilled sequence of *key reasoning tokens* identified by attention.  

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
  


