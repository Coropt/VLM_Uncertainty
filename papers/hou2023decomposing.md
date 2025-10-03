# Decomposing Uncertainty for Large Language Models through Input Clarification Ensembling  
**Authors:** Bairu Hou, Yujian Liu, Kaizhi Qian, Jacob Andreas, Shiyu Chang, Yang Zhang  
**Conference:** ICML 2024  

---

## Core Idea
This paper proposes **Input Clarification Ensembling (ICE)**, a framework to decompose the uncertainty of large language model (LLM) predictions.  
Instead of training multiple models (deep ensembles) or modifying model parameters (Bayesian neural networks), ICE works at the **input level** by generating clarifications for ambiguous inputs, feeding them into the LLM, and ensembling the predictions.

---

## Types of Uncertainty
- **Aleatoric uncertainty**: caused by input ambiguity or inherent randomness.  
- **Epistemic uncertainty**: caused by missing knowledge in the model, reducible with more data or training.  

---

## Key Equation
The decomposition is expressed as:

$$
H(q(Y|X)) = I(Y;C|X) + \mathbb{E}_{q(C|X)}\big[ H(q(Y|X \oplus C)) \big]
$$

where:  
- $I(Y;C|X)$ measures disagreement across clarifications → **aleatoric uncertainty**.  
- $\mathbb{E}[H(\cdot)]$ measures average entropy across clarified inputs → **epistemic uncertainty**.  

---

## Method
1. **Clarification Generation**: a clarification LLM (e.g., GPT-3.5, GPT-4, fine-tuned LLaMA-3) produces multiple clarified versions of the input.  
2. **Prediction Ensembling**: the target LLM produces outputs for each clarified input.  
3. **Uncertainty Decomposition**: total entropy is decomposed into aleatoric vs. epistemic components.  

---

## Experimental Findings
- **Total uncertainty** quantification is reliable (AUROC competitive with baselines like deep ensembles).  
- **Ambiguity detection** is significantly improved compared to semantic entropy and ASK-for-confidence methods.  
- **Monotonicity check** shows that clarified inputs reduce aleatoric uncertainty.  
- Improves **recall of correct answers** by presenting users with clarification options.  

---

## Contribution
- Provides a **black-box friendly** method for LLM uncertainty decomposition.  
- Offers clearer attribution of uncertainty: distinguishing **input ambiguity** vs. **model knowledge gaps**.  
- Improves **human–LLM interaction** by suggesting clarifications when inputs are underspecified.  

