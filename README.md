# Beyond Next-Token Prediction [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
A curated list of research studying the limitations/learning behavior of next-token prediction and methods that move beyond it.

The next-token prediction training paradigm has brought us significant breakthroughs in recent years. However, there is a growing body of work questioning its inductive biases, planning limitations, data efficiency, etc. Is next-token prediction really the end-all for language modeling? Are there expressive shortcomings to it? Are there ways to extract more gradients from existing datasets beyond the next token?

## Table of Contents
* [Methods](#methods)
    - [Multi-Token Prediction](#methods-mtp)
    - [Latent Prediction](#methods-latent)
    - [Diffusion Language Models](#methods-diffusion)
    - [Energy-based Models](#methods-energy)
* [Studies](#studies)
* [Surveys](#surveys)

## Contributing
If you know of a paper/blog related to this repository that I missed out on, feel free to open a pull request. Please follow this format when suggesting a new paper:
```
* **Paper Title** <br>
*Author(s)* <br>
Conference, Year. [[Paper]](link) [[Code]](link) [[Website]](link)
Summary (Optional): <short summary of the paper>
```

## <a name="methods"></a> Methods

### <a name="methods-mtp"></a> Multi-Token Prediction

* **ProphetNet: Predicting Future N-gram for Sequence-to-Sequence Pre-training** <br>
*Weizhen Qi, Yu Yan, Yeyun Gong, Dayiheng Liu, Nan Duan, Jiusheng Chen, Ruofei Zhang, Ming Zhou* <br>
EMNLP, 2020. [[Paper]](https://arxiv.org/abs/2001.04063)[[Code]](https://github.com/microsoft/ProphetNet/tree/master/ProphetNet) <details><summary>*Summary*</summary>AFAIK, first paper to introduce multi-token predictions</details>

* **Better & Faster Large Language Models via Multi-token Prediction** <br>
*Fabian Gloeckle, Badr Youbi Idrissi, Baptiste Rozière, David Lopez-Paz, Gabriel Synnaeve* <br>
ICML, 2024. [[Paper]](https://arxiv.org/abs/2404.19737) 