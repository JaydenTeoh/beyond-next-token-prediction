# Awesome Beyond Next-Token Prediction Papers [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
A curated list of research studying the limitations and learning dynamics of next-token prediction, as well as methods that move beyond it.

Next-token prediction has driven many of the breakthroughs in modern language modeling. Yet a growing body of work highlights its limitations such as its struggle with long-range planning and data inefficiency. Is next-token prediction truly the end-all objective for language modeling? What expressive shortcomings arise when models are trained only to predict the next token? Can we extract richer gradients from existing datasets beyond the next token?


## Table of Contents
* [Studies/Benchmarks](#studies)
* [Methods](#methods)
    - [Multi-Token Prediction Methods](#methods-mtp)
    - [Latent Prediction Methods](#methods-latent)
    - [Sequence Augmentation Techniques](#methods-seq-aug)
    - [Continuous Generation Methods](#methods-continuous)

## Contributing
If you know of a paper/blog related to this repository that we missed out on, feel free to open a pull request. Please follow this format when suggesting a new paper:
```
* **Paper Title** <br>
*Author(s)* <br>
Conference, Year. [[Paper]](link) [[Code]](link) [[Website]](link)
```

## <a name="studies"></a> Studies/Benchmarks

* **The Pitfalls of Next-Token Prediction** <br>
*Gregor Bachmann, Vaishnavh Nagarajan* <br>
ICML, 2024. [[Paper]](https://arxiv.org/abs/2403.06963) [[Code]](https://github.com/gregorbachmann/Next-Token-Failures)

* **The Factorization Curse: Which Tokens You Predict Underlie the Reversal Curse and More** <br>
*Ouail Kitouni, Niklas Nolte, Diane Bouchacourt, Adina Williams, Mike Rabbat, Mark Ibrahim* <br>
NeurIPS, 2024. [[Paper]](https://arxiv.org/abs/2406.05183)

* **Roll the dice & look before you leap: Going beyond the creative limits of next-token prediction** <br>
*Vaishnavh Nagarajan, Chen Henry Wu, Charles Ding, Aditi Raghunathan* <br>
ICML, 2025. [[Paper]](https://arxiv.org/abs/2504.15266) [[Code]](https://github.com/chenwu98/algorithmic-creativity)

* **Alternatives To Next Token Prediction In Text Generation — A Survey** <br>
*Charlie Wyatt, Aditya Joshi, Flora Salim* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2509.24435) 

* **Autoregressive Language Models are Secretly Energy-Based Models: Insights into the Lookahead Capabilities of Next-Token Prediction** <br>
*Mathieu Blondel, Michael E. Sander, Germain Vivier-Ardisson, Tianlin Liu, Vincent Roulet* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2512.15605) 

## <a name="methods"></a> Methods

**Clarification of scope:** We are primarily focused on foundational training methods that augment the learning objective and are broadly applicable during pretraining. We exclude methods that operate atop of a pretrained next-token prediction backbone, e.g., speculative decoding or finetuning-only methods.

### <a name="methods-mtp"></a> Multi-Token Prediction Methods
This section collates methods that **predict several future tokens using a shared model trunk**. For generality, we include any approach that augments the training objective with token-level losses beyond the next token, for e.g., future n-gram or forward-reverse predictions.

* **ProphetNet: Predicting Future N-gram for Sequence-to-Sequence Pre-training** <br>
*Weizhen Qi, Yu Yan, Yeyun Gong, Dayiheng Liu, Nan Duan, Jiusheng Chen, Ruofei Zhang, Ming Zhou* <br>
EMNLP, 2020. [[Paper]](https://arxiv.org/abs/2001.04063) [[Code]](https://github.com/microsoft/ProphetNet/tree/master/ProphetNet)

* **Better & Faster Large Language Models via Multi-token Prediction** <br>
*Fabian Gloeckle, Badr Youbi Idrissi, Baptiste Rozière, David Lopez-Paz, Gabriel Synnaeve* <br>
ICML, 2024. [[Paper]](https://arxiv.org/abs/2404.19737) 

* **DeepSeek-V3 Technical Report** <br>
*DeepSeek-AI* <br>
arXiv, 2024. [[Paper]](https://arxiv.org/abs/2412.19437) [[Code]](https://github.com/deepseek-ai/DeepSeek-V3) 

* **Efficient Joint Prediction of Multiple Future Tokens** <br>
*Kwangjun Ahn, Alex Lamb, John Langford* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2503.21801)

* **Improving Large Language Models with Concept-Aware Fine-Tuning** <br>
*Michael K. Chen, Xikun Zhang, Jiaxing Huang, Dacheng Tao* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2506.07833) [[Code]](https://github.com/michaelchen-lab/caft-llm)

* **Beyond Next Token Prediction: Patch-Level Training for Large Language Models** <br>
*Chenze Shao, Fandong Meng, Jie Zhou* <br>
ICLR, 2025. [[Paper]](https://arxiv.org/abs/2407.12665) [[Code]](https://github.com/shaochenze/PatchTrain) 

* **The Belief State Transformer** <br>
*Edward S. Hu, Kwangjun Ahn, Qinghua Liu, Haoran Xu, Manan Tomar, Ada Langford, Jayden Teoh, Bryon Xu, David Yan, Dinesh Jayaraman, Alex Lamb, John Langford* <br>
ICLR, 2025. [[Paper]](https://arxiv.org/abs/2410.23506) [[Code]](https://github.com/microsoft/bst) [[Website]](https://edwardshu.com/bst-website/)

* **Predicting the Order of Upcoming Tokens Improves Language Modeling** <br>
*Zayd M. K. Zuhri, Erland Hilman Fuadi, Alham Fikri Aji* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2508.19228) [[Code]](https://github.com/zaydzuhri/token-order-prediction) 

* **Multi-Token Prediction Needs Registers** <br>
*Anastasios Gerontopoulos, Spyros Gidaris, Nikos Komodakis* <br>
NeurIPS, 2025. [[Paper]](https://arxiv.org/abs/2505.10518) [[Code]](https://github.com/nasosger/MuToR) 


### <a name="methods-latent"></a> Latent Prediction Methods
We intentionally use “latent” in a broad sense here to keep the categorization simple. It may refer to final-layer hidden states, learned summaries of future tokens, conceptual embeddings of text, or other intermediate representations. As a rule of thumb, methods in this category incorporate auxiliary objectives to **reconstruct some latent representation of text during training**, rather than relying solely on token-level predictions.

* **Semformer: Transformer Language Models with Semantic Planning** <br>
*Yongjing Yin, Junran Ding, Kai Song, Yue Zhang* <br>
EMNLP, 2024. [[Paper]](https://arxiv.org/abs/2409.11143) [[Code]](https://github.com/ARIES-LM/Semformer.git) 

* **Large Concept Models: Language Modeling in a Sentence Representation Space** <br>
*Large Concept Models Team (FAIR at Meta)* <br>
arXiv, 2024. [[Paper]](https://arxiv.org/abs/2412.08821) [[Code]](https://github.com/facebookresearch/large_concept_model) 

* **LLM Pretraining with Continuous Concepts** <br>
*Jihoon Tack, Jack Lanchantin, Jane Yu, Andrew Cohen, Ilia Kulikov, Janice Lan, Shibo Hao, Yuandong Tian, Jason Weston, Xian Li* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2502.08524) [[Code]](https://github.com/facebookresearch/RAM/tree/main/projects/cocomix) 

* **Beyond Multi-Token Prediction: Pretraining LLMs with Future Summaries** <br>
*Divyat Mahajan, Sachin Goyal, Badr Youbi Idrissi, Mohammad Pezeshki, Ioannis Mitliagkas, David Lopez-Paz, Kartik Ahuja* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2510.14751) 

* **Continuous Autoregressive Language Models** <br>
*Chenze Shao, Darren Li, Fandong Meng, Jie Zhou* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2510.27688) [[Code]](https://github.com/shaochenze/calm) [[Website]](https://shaochenze.github.io/blog/2025/CALM) 

* **Next-Latent Prediction Transformers Learn Compact World Models** <br>
*Jayden Teoh, Manan Tomar, Kwangjun Ahn, Edward S. Hu, Pratyusha Sharma, Riashat Islam, Alex Lamb, John Langford* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2511.05963)

### <a name="methods-seq-aug"></a> Sequence Augmentation Techniques
This section covers methods that **augment training sequences** in ways that help overcome the myopic biases of standard next-token prediction.

* **Efficient Training of Language Models to Fill in the Middle** <br>
*Mohammad Bavarian, Heewoo Jun, Nikolas Tezak, John Schulman, Christine McLeavey, Jerry Tworek, Mark Chen* <br>
arXiv, 2022. [[Paper]](https://arxiv.org/abs/2207.14255)

* **σ-GPTs: A New Approach to Autoregressive
Models** <br>
*Arnaud Pannatier, Evann Courdier, François Fleuret* <br>
ECML, 2024. [[Paper]](https://arxiv.org/abs/2404.09562) [[Code]](https://github.com/idiap/sigma-gpt) 

* **Looking beyond the next token** <br>
*Abitha Thankaraj, Yiding Jiang, J. Zico Kolter, Yonatan Bisk* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2504.11336)

### <a name="methods-continuous"></a> Continuous Generation Methods
This section covers continuous generation methods, i.e., approaches that generate text by iteratively refining a global continuous representation of the entire output, such as through diffusion, flow matching, or energy minimization, rather than emitting each token directly in a single pass. We focus on notable continuous generation methods and papers demonstrating how they address limitations of next-token prediction.

Diffusion Language Models (DLM) are a rapidly growing area of research. We direct readers to this [repository](https://github.com/VILA-Lab/Awesome-DLMs/) for awesome curated list of DLM papers instead.


* **Discrete Flow Matching** <br>
*Itai Gat, Tal Remez, Neta Shaul, Felix Kreuk, Ricky T. Q. Chen, Gabriel Synnaeve, Yossi Adi, Yaron Lipman* <br>
NeurIPS, 2024. [[Paper]](https://arxiv.org/abs/2407.15595)

* **Diffusion Forcing: Next-token Prediction Meets Full-Sequence Diffusion** <br>
*Boyuan Chen, Diego Marti Monso, Yilun Du, Max Simchowitz, Russ Tedrake, Vincent Sitzmann* <br>
NeurIPS, 2024. [[Paper]](https://arxiv.org/abs/2407.01392) [[Code]](https://github.com/buoyancy99/diffusion-forcing) [[Website]](https://www.boyuan.space/diffusion-forcing/) 

* **Beyond Autoregression: Discrete Diffusion for Complex Reasoning and Planning** <br>
*Jiacheng Ye, Jiahui Gao, Shansan Gong, Lin Zheng, Xin Jiang, Zhenguo Li, Lingpeng Kong* <br>
ICLR, 2025. [[Paper]](https://arxiv.org/abs/2410.14157) [[Code]](https://github.com/HKUNLP/diffusion-vs-ar)

* **Block Diffusion: Interpolating Between Autoregressive and Diffusion Language Models** <br>
*Marianne Arriola, Aaron Gokaslan, Justin T. Chiu, Zhihan Yang, Zhixuan Qi, Jiaqi Han, Subham Sekhar Sahoo, Volodymyr Kuleshov* <br>
ICLR, 2025. [[Paper]](https://arxiv.org/abs/2503.09573) [[Code]](https://github.com/kuleshov-group/bd3lms) [[Website]](https://m-arriola.com/bd3lms/) 

* **Large Language Diffusion Models** <br>
*Shen Nie, Fengqi Zhu, Zebin You, Xiaolu Zhang, Jingyang Ou, Jun Hu, Jun Zhou, Yankai Lin, Ji-Rong Wen, Chongxuan Li* <br>
NeurIPS, 2025. [[Paper]](https://arxiv.org/abs/2502.09992) [[Code]](https://github.com/ML-GSAI/LLaDA) [[Website]](https://ml-gsai.github.io/LLaDA-demo/) 

* **Energy-Based Transformers are Scalable Learners and Thinkers** <br>
*Alexi Gladstone, Ganesh Nanduru, Md Mofijul Islam, Peixuan Han, Hyeonjeong Ha, Aman Chadha, Yilun Du, Heng Ji, Jundong Li, Tariq Iqbal* <br>
arXiv, 2025. [[Paper]](https://arxiv.org/abs/2507.02092) [[Code]](https://github.com/alexiglad/ebt) [[Website]](https://energy-based-transformers.github.io/) 
