# 💡How to Train Frontier Models Effectively?

**Author:** **Yifan Zhang**

**Date:** December 21, 2025

1. Pretrain a gigantic MoE model from scratch using a full attention model (GQA or TPA https://arxiv.org/abs/2501.06425 [1]) mixed with some shortSWA (https://yifanzhang-pro.github.io/Rethinking-SWA/, used in GPT-OSS) or (Higher) Linear Attention (https://arxiv.org/abs/2510.27258 [2]) and [To-be-announced] equipped with Multi-token Prediction (MTP), which we call Pro-Base. Notably, please replace RoPE with Multiplicative GRAPE combined with additive position encodings, such as Additive GRAPE and Alibi (https://arxiv.org/abs/2512.07805 [3])!

2. Midtrain the Pro-Base model using High-quality STEM datasets, such as AutoMathText (https://arxiv.org/abs/2402.07625 [4]) and AutoMathText-V2 (https://iiis-ai.github.io/AutoMathText-V2), 2.4T unique tokens, used in Kimi K2.5 and Kimi K3), which we call Pro.

3. Perform large-scale Reinforcement Learning on this gigantic model using (KL-Regularized) Policy Gradients (RPG: https://arxiv.org/abs/2505.17508 [5]), which we call Pro-Instruct.

4. Distillation Pretraining: Train the Flash model (using sparse attention and linear attention) using Pro and Pro-Instruct logits as targets with a KL loss using the Pretraining Framework of the FSDP2.

5. On-Policy Distillation during mid-training or post-training on Flash, using online rollouts with a KL loss (using KL-Regularized Policy Gradient without Reward https://arxiv.org/abs/2505.17508 [5]) using a true on-policy Reinforcement Learning framework.

6. Reinforcement Learning on this Flash Model using KL-Regularized Policy Gradient and REINFORCE-estimator (https://arxiv.org/abs/2505.17508 [5]) with Verifiable Reward (such as MathQA https://arxiv.org/abs/2401.09003 [6]) and Verifiable Progress Reward (Language Server: https://arxiv.org/abs/2510.22907 [9]), General Preference Models (GPM https://arxiv.org/abs/2410.02197 [7]), and Generative Verifiers (Cumulative Reasoning: https://arxiv.org/pdf/2308.04371 [8] and DeepSeek-Math-V2)!

This is what you need!

### References

1. **Tensor Product Attention Is All You Need**

**Yifan Zhang***, Yifeng Liu*, Huizhuo Yuan, Zhen Qin, Yang Yuan, Quanquan Gu, Andrew C Yao

Conference on Neural Information Processing Systems (NeurIPS 2025 Spotlight)

2. **Higher-order Linear Attention**

**Yifan Zhang**, Zhen Qin, Quanquan Gu

arXiv:2510.27258

3. **Group Representational Position Encoding**

**Yifan Zhang**, Zixiang Chen, Yifeng Liu, Zhen Qin, Huizhuo Yuan, Kangping Xu, Yang Yuan, Quanquan Gu, Andrew C Yao

arXiv:2512.07805

4. **Autonomous Data Selection with Zero-shot Generative Classifiers for Mathematical Texts** 

**Yifan Zhang***, Yifan Luo*, Yang Yuan, Andrew C Yao

Findings of the Association for Computational Linguistics (ACL 2025 Findings)

5. **On the Design of KL-Regularized Policy Gradient Algorithms for LLM Reasoning** 

**Yifan Zhang***, Yifeng Liu*, Huizhuo Yuan, Yang Yuan, Quanquan Gu, Andrew C Yao

Conference on Neural Information Processing Systems (NeurIPS 2025 MATH-AI Workshop); See also Thinking Machines Tinker and DeepSeek V3.2

6. **Augmenting Math Word Problems via Iterative Question Composing** 

Haoxiong Liu*, **Yifan Zhang***, Yifan Luo, Andrew C Yao

AAAI Conference on Artificial Intelligence (AAAI 2025)

7. **Beyond Bradley-Terry Models: A General Preference Model for Language Model Alignment**  

**Yifan Zhang***, Ge Zhang*, Yue Wu*, Kangping Xu, Quanquan Gu

International Conference on Machine Learning (ICML 2025)

8. **Cumulative Reasoning with Large Language Models** 

**Yifan Zhang***, Jingqin Yang*, Yang Yuan, Andrew C Yao

Transactions on Machine Learning Research (TMLR) 

9. **Language Server CLI Empowers Language Agents with Process Rewards** 

**Yifan Zhang**, et al.

arXiv:2510.22907, see also Claude Code v2.0.74
