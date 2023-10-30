<p align="center"> <img src="images/devops_eval_logo.png" style="width: 100%;" id="title-icon">       </p>

<p align="center">
  🤗 <a href="https://huggingface.co/datasets/codefuse-admin/devopseval-exam" target="_blank">Hugging Face</a> • ⏬ <a href="#data" target="_blank">数据</a> • 📖 <a href="resources/tutorial_zh.md" target="_blank">教程</a>
  <br>
  <a href="https://github.com/codefuse-ai/codefuse-devops-eval/blob/main/README.md"> English</a> | <a href="https://github.com/codefuse-ai/codefuse-devops-eval/blob/main/README_zh.md"> 中文 </a>
</p>

DevOps-Eval是一个专门为DevOps领域大模型设计的综合评估数据集。我们希望DevOps-Eval能够帮助开发者，尤其是DevOps领域的开发者，追踪进展并分析他们拥有的DevOps大模型的优势和不足之处。

📚 该仓库包含与DevOps和AIOps相关的问题和练习。

💥 目前有 4850 个多项选择题，根据DevOps的通用流程将其归纳未8个模块，如[下图](images/data_info.png)所示。

🔥 AIOps子类当前已有中英文样本2200例，覆盖的场景包括**日志解析**、**时序异常检测**、**时序分类**和**根因分析**。


<p align="center"> <a href="resources/devops_diagram_zh.jpg"> <img src="images/data_info.png" style="width: 100%;" id="data_info"></a></p>


## 🔔 更新
* **[2023.10.25]** 增加AIOps样本，包含日志解析、时序异常检测、时序分类和根因分析
* **[2023.10.18]** DevOps-Eval发布大模型评测排行版
<br>

## 📜 目录

- [🏆 排行榜](#-排行榜)
  - [👀 DevOps](#-devops)
  - [🔥 AIOps](#-aiops)
- [⏬ 数据](#-数据)
  - [👀 说明](#-说明)
  - [🔥 AIOps样本示例](#-AIOps样本示例)
- [🚀 如何进行测试](#-如何进行测试)
- [🧭 TODO](#-todo)
- [🏁 Licenses](#-licenses)
- [😃 引用](#-引用)

## 🏆 排行榜
以下是我们获得的初版评测结果，包括多个开源模型的zero-shot和five-shot准确率。我们注意到，对于大多数指令模型来说，five-shot的准确率要优于zero-shot。

### DevOps
#### Zero Shot

| **模型**                 | plan  | code  | build | test  | release | deploy | operate | monitor |  **平均分**  |
|:------------------------:|:-----:|:-----:|:-----:|:------:|:--------:|:------:|:-------:|:--------:|:---------:|
| **DevOpsPal-14B-Chat** | 60.61 | 78.35 | 84.86 | 84.65 | 87.26 | 82.75 | 81.34 | 79.17 | **80.34** |
| **DevOpsPal-14B-Base** | 54.55 | 77.82 | 83.49 | 85.96 | 86.32 | 81.96 | 85.82 | 82.41 | **80.26** |
| Qwen-14B-Chat          |  60.61 | 75.4 | 85.32 | 84.21 | 89.62 | 82.75 | 83.58 | 80.56 |   79.28   |
| Qwen-14B-Base          |  57.58 | 73.81 | 84.4 | 85.53 | 86.32 | 81.18 | 82.09 | 80.09 |   77.92   |
| Baichuan2-13B-Base     |  60.61 | 69.42 | 79.82 | 79.82 | 82.55 | 81.18 | 85.07 | 83.8 |   75.10   |
| Baichuan2-13B-Chat     | 60.61 | 68.43 | 77.98 | 80.7 | 81.6 | 83.53 | 82.09 | 84.72 |   74.60   |
| **DevOpsPal-7B-Chat**  | 54.55 | 69.11 | 83.94 | 82.02 | 76.89 | 80 | 79.85 | 77.78 | **74.00** |
| **DevOpsPal-7B-Base**  | 54.55 | 68.96 | 82.11 | 78.95 | 80.66 | 76.47 | 79.85 | 78.7 | **73.55** |
| Qwen-7B-Base           | 53.03 | 68.13 | 78.9 | 75.44 | 80.19 | 80 | 83.58 | 80.09 |   73.13   |
| Qwen-7B-Chat           | 57.58 | 66.01 | 80.28 | 79.82 | 76.89 | 77.65 | 80.6 | 79.17 |   71.96   |
| Baichuan2-7B-Chat      |  54.55 | 63.66 | 77.98 | 76.32 | 71.7 | 73.33 | 75.37 | 79.63 |   68.17   |
| Internlm-7B-Chat       |  60.61 | 62.15 | 77.06 | 76.32 | 66.98 | 74.51 | 74.63 | 78.24 |   68.08   |
| Baichuan2-7B-Base      |  56.06 | 62.45 | 75.69 | 70.61 | 74.06 | 69.8 | 76.12 | 75.93 |   67.51   |
| Internlm-7B-Base       |  54.55 | 58.29 | 79.36 | 78.95 | 77.83 | 70.59 | 78.36 | 75.93 |   66.91   |


#### Five Shot

| **模型**                 | plan  | code  | build | test  | release | deploy | operate | monitor | **平均分**    |
|:------------------------:|:-----:|:-----:|:-----:|:------:|:--------:|:------:|:-------:|:--------:|:---------:|
| **DevOpsPal-14B-Chat** |63.64 | 79.49 | 81.65 | 85.96 | 86.79 | 86.67 | 89.55 | 81.48 | **81.77** |
| **DevOpsPal-14B-Base** |  62.12 | 80.55 | 82.57 | 85.53 | 85.85 | 84.71 | 85.07 | 80.09 | **81.70** |
| Qwen-14B-Chat |  65.15 | 76 | 82.57 | 85.53 | 84.91 | 84.31 | 85.82 | 81.48 | 79.55 |
| Qwen-14B-Base |  66.67 | 76.15 | 84.4 | 85.53 | 86.32 | 80.39 | 86.57 | 80.56 | 79.51 |
| Baichuan2-13B-Base | 63.64 | 71.39 | 80.73 | 82.46 | 81.13 | 84.31 | 91.79 | 85.19 | 77.09 |
| Qwen-7B-Base | 75.76 | 72.52 | 78.9 | 81.14 | 83.96 | 81.18 | 85.07 | 81.94 | 77.02 |
| Baichuan2-13B-Chat | 62.12 | 69.95 | 76.61 | 84.21 | 83.49 | 79.61 | 88.06 | 80.56 | 75.32 |
| **DevOpsPal-7B-Chat** | 66.67 | 69.95 | 83.94 | 81.14 | 80.19 | 82.75 | 82.84 | 76.85 | **75.25** |
| **DevOpsPal-7B-Base** |  69.7 | 69.49 | 82.11 | 81.14 | 82.55 | 82.35 | 80.6 | 79.17 | **75.17** |
| Qwen-7B-Chat |  65.15 | 66.54 | 82.57 | 81.58 | 81.6 | 81.18 | 80.6 | 81.02 | 73.62 |
| Baichuan2-7B-Base | 60.61 | 67.22 | 76.61 | 75 | 77.83 | 78.43 | 80.6 | 79.63 | 72.11 |
| Internlm-7B-Chat |  60.61 | 63.06 | 79.82 | 80.26 | 67.92 | 75.69 | 73.88 | 77.31 | 71.09 |
| Baichuan2-7B-Chat |  60.61 | 64.95 | 81.19 | 75.88 | 71.23 | 75.69 | 78.36 | 79.17 | 70.49 |
| Internlm-7B-Base |  62.12 | 65.25 | 77.52 | 80.7 | 74.06 | 78.82 | 79.85 | 75.46 | 69.17 |


### AIOps
#### Zero Shot
|    **模型**    | 日志解析  | 根因分析 | 时序异常检测 | 时序分类 | **平均分** |
|:-------------------:|:-----:|:----:|:------:|:----:|:-------:|
|    Qwen-14B-Base    | 66.29 | 58.8 | 25.33  | 43.5 |  49.27  |
| DevOpsPal-14B—Base  | 63.14 | 53.6 | 23.33  | 43.5 |  46.55  |
| DevOpsPal-14B—Chat  |  60   |  56  |   24   |  43  |  46.18  |
|    Qwen-14B-Chat    | 64.57 | 51.6 | 22.67  |  36  |   45    |
|    Qwen-7B-Base     |  50   | 39.2 | 22.67  |  54  |  40.82  |
|    Qwen-7B-Chat     | 57.43 | 38.8 | 22.33  | 39.5 |  40.36  |
|  DevOpsPal-7B—Chat  | 56.57 | 30.4 | 25.33  |  45  |   40    |
| Baichuan2-13B-Chat  |  64   |  18  | 21.33  | 37.5 |  37.09  |
|  Baichuan2-7B-Chat  | 60.86 |  10  |   28   | 34.5 |  35.55  |
|  Baichuan2-7B-Base  | 53.43 | 12.8 | 27.67  | 36.5 |  34.09  |
|  Internlm-7B—Base   | 48.57 | 18.8 | 23.33  | 37.5 |  32.91  |
| Baichuan2-13B-Base  |  54   | 12.4 |   23   | 34.5 |  32.55  |
|  DevOpsPal-7B—Base  | 46.57 | 20.8 |   25   |  34  |  32.55  |
|  Internlm-7B—Chat   | 58.86 | 8.8  | 22.33  | 28.5 |   32    |

#### One Shot
|    **模型**    |  日志解析  | 根因分析  | 时序异常检测  | 时序分类  | **平均分** |
|:-------------------:|:------------:|:------------------:|:---------------------------:|:-------------------------:|:-------:|
| DevOpsPal-14B—Chat | 66.29 | 80.8 | 23.33 | 44.5 | 53.91 |
| Qwen-14B-Base | 64.29 | 74.4 | 28 | 48.5 | 53.82 |
| DevOpsPal-14B—Base | 60 | 74 | 25.33 | 43.5 | 50.73 |
| Qwen-14B-Chat | 49.71 | 65.6 | 28.67 | 48 | 47.27 |
| Qwen-7B-Base | 56 | 60.8 | 27.67 | 44 | 47.18 |
| DevOpsPal-7B—Base | 52.86 | 44.4 | 28 | 44.5 | 42.64 |
| Qwen-7B-Chat | 54.57 | 52 | 29.67 | 26.5 | 42.09 |
| Baichuan2-13B-Base | 56 | 43.2 | 24.33 | 41 | 41.73 |
| Baichuan2-13B-Chat | 57.43 | 44.4 | 25 | 25.5 | 39.82 |
| Baichuan2-7B-Base | 48.29 | 40.4 | 27 | 42 | 39.55 |
| Baichuan2-7B-Chat | 58.57 | 31.6 | 27 | 31.5 | 38.91 |
| DevOpsPal-7B—Chat | 56.57 | 27.2 | 25.33 | 41.5 | 38.64 |
| Internlm-7B—Base | 48 | 33.2 | 29 | 35 | 37.09 |
| Internlm-7B—Chat | 62.57 | 12.8 | 22.33 | 21 | 32.73 |

## ⏬ 数据
#### 下载
* 方法一：下载zip压缩文件（你也可以直接用浏览器打开下面的链接）：
  ```
  wget https://huggingface.co/datasets/codefuse-admin/devopseval-exam/resolve/main/devopseval-exam.zip
  ```
  然后可以使用 pandas加载数据：

  ```
  import os
  import pandas as pd
  
  File_Dir="devopseval-exam"
  test_df=pd.read_csv(os.path.join(File_Dir,"test","UnitTesting.csv"))
  ```
* 方法二：使用[Hugging Face datasets](https://huggingface.co/datasets/codefuse-admin/devopseval-exam)直接加载数据集。示例如下：
  ```python
  from datasets import load_dataset
  dataset=load_dataset(r"DevOps-Eval/devopseval-exam",name="UnitTesting")
  
  print(dataset['val'][0])
  # {"id": 1, "question": "单元测试应该覆盖以下哪些方面？", "A": "正常路径", "B": "异常路径", "C": "边界值条件"，"D": 所有以上，"answer": "D", "explanation": ""}  ```
#### 👀 说明
为了方便使用，我们已经整理出了 53 个细分类别以及它们的中英文名称。具体细节请查看 [category_mapping.json](resources/categroy_mapping.json) 。格式如下：

```
{
  "UnitTesting.csv": [
    "unit testing",
    "单元测试",
    {"dev": 5, "test": 32}
    "TEST"
  ],
  ...
  "file_name":[
  "英文名称",
  "中文名称",
  "样本数量",
  "类别(PLAN,CODE,BUILD,TEST,RELEASE,DEPOLY,OPERATE,MONITOR八选一)"
  ]
}
```
每个细分类别由两个部分组成：dev 和 test。每个细分类别的 dev 集包含五个示范实例以及为 few-shot 评估提供的解释。而 test 集则用于模型评估，并且test数据已包含准确标签。

下面是 dev 数据的示例，来自"版本控制"细分类别：
```
id: 4
question: 如何找到Git特定提交中已更改的文件列表？
A: 使用命令 `git diff --name-only SHA`
B: 使用命令 `git log --name-only SHA`
C: 使用命令 `git commit --name-only SHA`
D: 使用命令 `git clone --name-only SHA`
answer: A
explanation: 
分析原因：
git diff --name-only SHA命令会显示与SHA参数对应的提交中已修改的文件列表。参数--name-only让命令只输出文件名，而忽略其他信息。其它选项中的命令并不能实现此功能。
```
#### 🔥 AIOps样本示例
👀 👀 此处以日志解析和时序异常检测为例，对AIOps样本做一些简要的展示:

日志解析
```
id: 0
question:
下面是一些运行日志
 0 04:21:15,429 WARN Cannot open channel to 2 at election address /10.10.34.12:3888
 1 19:18:56,377 WARN ******* GOODBYE /10.10.34.11:52703 ********
 2 19:13:46,128 WARN ******* GOODBYE /10.10.34.11:52308 ********
 3 19:16:26,268 WARN ******* GOODBYE /10.10.34.11:52502 ********
 4 09:11:16,012 WARN Cannot open channel to 3 at election address /10.10.34.13:3888
 5 16:37:13,837 WARN Cannot open channel to 2 at election address /10.10.34.12:3888
 6 09:09:16,008 WARN Cannot open channel to 3 at election address /10.10.34.13:3888
 7 15:27:03,681 WARN Cannot open channel to 3 at election address /10.10.34.13:3888
日志最前面三部分别为序号、时间戳和日志Level，在不考虑这三部分内容的情况下，此处我们设定日志的变量用'<*>'代替，token与token之间用空格分隔，那么请问上述日志的日志模版具体是什么？
A: Notification time out: <*> 和 Connection broken for id <*>, my id = <*>, error =
B: Send worker leaving thread 和 Connection broken for id <*>, my id = <*>, error =
C: Received connection request /<*>:<*> 和 Interrupting SendWorker
D: Cannot open channel to <*> at election address /<*>:<*> 和 ******* GOODBYE /<*>:<*> ********
answer: D
explanation: 根据日志中的内容，选项D是最符合日志模板的。日志中包含了"Cannot open channel to &lt;*&gt; at election address /&lt;*&gt;:&lt;*&gt;"和"******* GOODBYE /&lt;*&gt;:&lt;*&gt; ********"这两个固定的模板片段，它们都在选项D中出现了。同时，其他选项中的模板片段与日志中的内容不匹配。因此，选项D是最符合日志模板的。
```
时序异常检测
```
id: 0
question:
分析如下时间序列
[50,62,74,84,92,97,99,98,94,87,77,65,265,40,28,17,8,3,0,0,4,10,20,31,43,56,68,79,89,95,99,99,96,91,82,71,59,46,34,22,12,5,1,0,2,7,15,25,37,49]
请找出其中明显异常点的下标。所谓的异常点一般指的是明显与数据整体趋势不符的点。
A: 46
B: 0
C: 37
D: 12
answer: D
explanation: 根据分析，题目中的时间序列在12点出的值265要明显大于周围数据，存在着突增现象，因此选择D是正确的。
```

## 🚀 如何进行测试
如果需要在自己的 HuggingFace 格式的模型上进行测试的话，总的步骤分为如下几步:
1. 编写 Model 的 loader 函数
2. 编写 Model 的 context_builder 函数
3. 注册模型到配置文件中
4. 执行测试脚本
如果模型在加载进来后不需要特殊的处理，而且输入也不需要转换为特定的格式（e.g. chatml 格式或者其他的 human-bot 格式），请直接跳转到第四步直接发起测试。

#### 1. 编写 loader 函数
模型加载时还需要做一些额外的处理（e.g. tokenizer 调整），需要继承 `ModelAndTokenizerLoader` 类来覆写对应的 `load_model` 和 `load_tokenizer` 函数， 如下所示：
```python
class QwenModelAndTokenizerLoader(ModelAndTokenizerLoader):
    def __init__(self):
        super().__init__()
        pass
    
    @override
    def load_model(self, model_path: str):
    # Implementation of the method
        pass
    
    @override
    def load_tokenizer(self, model_path: str):
    # Implementation of the method
        pass
```
#### 2. 编写 Model 的 context_builder 函数
如果输入需要转换为特定的格式（e.g. chatml 格式或者其他的 human-bot 格式），则需要继承 ContextBuilder 类来覆写 make_context 函数，如下所示：
```python
class QwenChatContextBuilder(ContextBuilder):
    def __init__(self):
        super().__init__()
        
    @override
    def make_context(self, model, tokenizer, query: str, system: str = "hello！"):
    # Implementation of the method
        pass
```
#### 3. 注册模型到配置文件中
去 conf 中的 `model_conf.json`，注册对应的模型名和这个模型将要使用的 loader 和 context_builder，示例如下：
```json
{
  "Qwen-Chat": {
  "loader": "QwenModelAndTokenizerLoader",
  "context_builder": "QwenChatContextBuilder"
  }
}
```

#### 4. 执行测试脚本
直接运行以下代码发起测试
```Bash
python src/run_eval.py \
--model_path path_to_model \
--model_name model_name_in_conf \
--model_conf_path path_to_model_conf \
--eval_dataset_list all \
--eval_dataset_fp_conf_path path_to_dataset_conf \
--eval_dataset_type test \
--data_path path_to_downloaded_devops_eval_data \
--k_shot 0
```
👀 👀 具体评测流程见📖 [**数据集评测教程**](resources/tutorial_zh.md)
<br>

## 🧭 TODO
- [x] 添加AIOps样本
- [ ] 添加AIOps场景，比如**时间预测**
- [ ] 当前各类别样本量不平均，后续进一步增加样本数量
- [ ] 增加困难程度的样本集
- [ ] 增加样本的英文版本

<br>
<br>

## 🏁 Licenses
This project is licensed under the [Apache License (Version 2.0)](LICENSE.md).

<br>

## 😃 引用

如果您使用了我们的数据集，请引用我们的论文。
Coming soon...

<br>
<br>
