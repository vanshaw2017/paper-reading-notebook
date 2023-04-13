# https://www.promptingguide.ai/ 学习笔记
## 介绍
## 技术
* zero-shot prompting
* few-shot Prompting
* chain-of-thought Prompting 
  * 使用场景：算数、常识推理
  * zero-shot cot: "let's think step by step" 威力无穷
* self-consistency Prompting 
  * 使用场景：替换cot中使用的简单贪心解码 其想法是通过少样本CoT采样多个不同的推理路径，并使用生成结果选择最一致的答案。这有助于提高CoT提示在涉及算术和常识推理的任务中的性能。
  * 步骤：采样，多个输出，取输出最多的答案
* Generate Knowledge prompt:
  * 应用：输入问题的同时，输入一些相关知识
* Automatic Prompt engineering:
  * 自动Prompt生成：
    * AutoPrompt: https://arxiv.org/abs/2010.15980
    * Prefix Tuning: https://arxiv.org/abs/2101.00190
    * Prompt Tuning: https://arxiv.org/abs/2104.08691
* Directional Stimulus Prompting
  * 应用：给一些提示线索
  * 提问：这个和Generate Knowledge Prompt 思路有什么区别？
* React框架
  * Reason + act
* multi-moddal cot
  * 多模态COT：加入视觉信息
* Graph Prompting
## 应用
* PAL（Program-aided Language Models）
  * 加上程序化的提示语言，模仿Python执行器
  * 例子：时间Prompt
* generating Data
  * 用LLMs来生成各种数据
* Granduate Job Classification Case Study
  * 内容：对中等规模的线上文本分类使用Prompt-engineering的案例分析（比对各种Prompt方案），这个文本分类的主要任务是识别一个工作是否是入门级的工作，是否适合刚毕业的大学生
  * 结论
    * LLMs强于其他所有语言模型。even strong baseline DEBERTa-v3
    * 对于不需要专业知识任务，few-shot的Prompt的效果差于zero-shot。
    * Prompt工程对引出正确答案的作用很大：直接问让模型进行分类的f1 65.6,有Prompt的f1值达到了91.7.
    * 所有情况中，尝试让模型遵循模板效果不好
    * 许多小小的修改对结果有很大的影响：
      * 给出正确的提示，并且重复强调关键点似乎对结果最有帮助。
      * 简单地给模型一个(人类的)名字并这样称呼它，可以将F1分数提高0.6个百分点。
## 模型
* Flan
  * scaling instruction finetuning: 
    * scaling the number of tasks (1.8K tasks), 
    * scaling model size, 
    * and finetuning on chain-of-thought data (9 datasets used).
  * finetuning procedure:
    * 1.8K tasks were phrased as instructions and used to finetune the model
    * Uses both with and without exemplars(shot), and with and without CoT
  * capabilities and results:
    * 任务数量和模型扩大有利于指令fitune扩大化。所以需要继续扩大任务数量和模型规模。
    * fitune中增加COT数据集能让推理任务取得好结果。
    * Flank-PaLm提高多语言的能力。
    * Plan-PalM 在开放问题答案生成中表现良好。这也给实际使用中提供了好的参考。
* Chatgpt
* LLaMA 
  * This paper introduces a collection of foundation language models ranging from 7B to 65B parameters.
  *  given a compute budget smaller models trained on a lot more data can achieve better performance than the larger counterparts
  *  LLaMA-13B outperform GPT-3(175B) on many benchmarks despite being 10x smaller and possible to run a single GPU.
* GPT4
  * system messages:This can accelerate personalization and getting accurate and more precise results for specific use cases.
## Risks and Misuses


