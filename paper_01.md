# Pre-train, Prompt, and Predict: A Systematic Survey of Prompting Methods in Natural Language Processing 
## abstrct
(1)input x: prompt : x' with unfilled slot  -> x^ to derive y
introduce the basics of this promising paradigm </br>
(2)describe a unifiedset of mathematical notations that can cover a wide variety of existing work 用数学公式归纳</br>
(3)organize existing workalong several dimensions 把已有的工作按照维度分类</br>

# Two Sea Changes in NLP 两次巨变
全监督学习：早期语言模型比较依赖于特征工程
sea change 1 ->2017-2019 pretrain,finetune 
sea change 2 ->2021 pretrain,prompt,predict 
好处：给对了Prompt,一次模型训练训练可以用于很多任务。
catch（陷阱）：引入另一个问题，Prompt工程

# A Formal Description of Prompting prompting的形式化描述
## Supervised Learning in NLP   NLP中的有监督学习
P(y|x;θ)
## Prompting Basics prompting 基础
prompt addition
    x′=f_prompt(x)
    consist two slots:
    (1)input slot [X] and answer slot[Z]
    (2)fill slot [X] with the input x
    cloze prompt: prompt with slot to fill in the middle of text
    prefix prompt: the input text comes entirely before z

answer search 
    在语言模型中求Prompt的概率
answer mapping
    把【z】做映射
## Design Considerations for Prompting
* 预训练模型选择:如何选择预训练语言模型
* Prompt 工程:如何选择正确的Prompt
* Answer 工程：
* 范式扩展：扩展基本范式，提高效果
* 基于Prompt的模型训练策略:

# Pre-trained Language Models 预训练语言模型
## trainning objectives 训练目标
SLM(标准语言模型):
* denoising objectives 降噪
  * Corrupted Text Reconstruction:目标是将引入噪声的句子恢复到原本的样子，损失只计算引入噪声部分
  * Full Text Reconstruction (FTR)：整个句子都要计算损失
## Noising Functions
* masking：用【mask】去替换
* repalcement:和masking比较像，只是masking用【mask】去替换，而replacement用别的词去替换
* deletion:通常和ftr损失结合着用
* permutation:切分打乱重组
## directionality of representation
* left-to-right:从左往右
* bidirectional:双向拓展
* mix
## typical pretraining methods 典型的语言模型
* left2right:auto-regressive
* masked language models:双向
* prefix and encoder-decoder
  * Prefix Language Model
  * encoder-decoder 
  
# Prompt Engineering Prompt工程
Prompt engineering就是构造prompt 函数使得引入Prompt后的下游任务有最好的效果的这个过程，包括 Prompt template engineering。首先需要考虑Prompt的形状，其次考虑收工会这自动的方法开构建想要的prompt 形状。
* Prompt Shape
  *   cloze prompt:masked LMs, Fulltext reconstruction models
  *   prefix prompt:generation/standard , Fulltext reconstruction modelsauto-regressive LM,
* Manual Template Engineering 手工模板工程
* Automated Template Learning 自动模板学习
  * discrete Prompts: an actual text string
    * Prompt Mining: Frequent middle words or dependency paths can serve as a template as in “[X]middle words[Z]”
    * Prompt  Paraphrasing:seed prompt paraphrase it into a set of other candidate prompts(paraphraseing:translation into other language and then back ;using replacement from  thesauru; a neural prompt rewriter specifically optimized)
    * Gradient-based Search:applied a gradient-based search over actual tokens to findshort sequences that can trigger the underlying pre-trained LM to generate the desired target prediction
    * Prompt Generation:generation of prompts as a text generation task and use standardnatural language generation models to perform this task
    * Prompt Scoring: design atemplate for an input (head-relation-tail triple) using LMs,then score those filled prompts, selecting the one with the highest LM probability
  * continuous prompts: embedding space
    * remove two constraints:
      * relax the constraint that the embeddings of template words be the embeddings of natural language (e.g., English)words. 
      * Remove the restriction that the template is parameterized by the pre-trained LM’s parameters
    * Prefix Tuning： a method that prepends a sequence of continuoustask-specific vectors to the input,  while keeping the LM parameters frozen.
    * # todo 下来把这块的论文读一下
    * $$ {\sideset{}{}{max}_\phi} logP\left ( y\mid x;\theta ;\phi  \right ) ={\sideset{}{}{max}_\phi} \sum_{y_i}^{} logP\left ( y_i\mid h_{<i};\theta ;\phi  \right ) 
  * static or dynamic 

# Answer Engineering 
* Answer Shape
  * Tokens
  * Span
  * sentence
* Answer design method

# Multi—Prompt Learning 

# Training Strategies for Prompting Methods  Prompt学习的训练策略

# Application 应用

# Prompt-relevant Topics prompt相关的话题

# Challenges

# Meta Analysis

# Conclusion


