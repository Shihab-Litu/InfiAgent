<h1 align="center">
<img src="../../images/infiagent_logo.png" width="100" alt="ADA" />
<br>
InfiAgent-DABench: Evaluating Agents on Data Analysis Tasks
</h1>


<div align="center">

![](https://img.shields.io/badge/Code%20License-Apache_2.0-green.svg)
![](https://img.shields.io/badge/Data%20License-CC%20By%20NC%204.0-red.svg)
![](https://img.shields.io/badge/python-3.9+-blue.svg)
![](https://img.shields.io/badge/code%20style-black-000000.svg)

</div>

<!-- 
[![Code License](https://img.shields.io/badge/Code%20License-Apache_2.0-green.svg)](https://github.com/InfiAgent/ADA-agent/blob/main/LICENSE)
[![Data License](https://img.shields.io/badge/Data%20License-CC%20By%20NC%204.0-red.svg)]
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)]
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)] -->

<p align="center">
  <a href="https://infiagent.github.io/"><b>[🌐 Website]</b></a> •
  <a href="https://arxiv.org/abs/2401.05507"><b>[📜 Paper]</b></a> •
  <a href=""><b>[🤗 HF Models]</b></a> •
  <a href="https://github.com/InfiAgent/InfiAgent"><b>[🐱 GitHub]</b></a>
  <!-- <a href="https://9557c5365a6f44dc84.gradio.live"><b>[🐯 Gradio Demo]</b></a> -->
  <br>
  <!-- <a href="#-quick-start">Quick Start</a> • -->
  <!-- <a href="#%EF%B8%8F-citation">Citation</a> -->
</p>



| Rank | Model Name                  | Accuracy by Questions (%) | Proportional Accuracy by Subquestions (%) | Accuracy by Subquestions (%) |
| ---- | --------------------------- | ------------------------- | ----------------------------------------- | ---------------------------- |
| 1    | gpt-4-0613                  | 74.60                     | 78.72                                     | 79.01                        |
| 2    | daagent-34b                 | 60.77                     | 67.50                                     | 62.98                        |
| 3    | abab5.5-chat                | 60.13                     | 65.94                                     | 64.27                        |
| 4    | gpt-3.5-turbo-0613          | 58.20                     | 65.70                                     | 61.88                        |
| 5    | qwen-72b-chat               | 57.56                     | 62.46                                     | 56.17                        |
| 6    | daagent-13b                 | 54.52                     | 60.51                                     | 55.72                        |
| 7    | gemini-pro                  | 53.38                     | 58.32                                     | 51.93                        |
| 8    | mixtral-8x7b-instruct-v0.1  | 49.20                     | 54.02                                     | 51.38                        |
| 9    | daagent-7b                  | 49.02                     | 57.63                                     | 54.19                        |
| 10   | deepseek-coder-33b-instruct | 44.84                     | 48.90                                     | 46.31                        |
| 11   | claude-2.1                  | 43.41                     | 49.65                                     | 46.96                        |
| 12   | phind-codellama-34b-v2      | 42.02                     | 47.41                                     | 44.40                        |
| 13   | xwincoder-34b               | 39.87                     | 45.46                                     | 42.73                        |
| 14   | mistral-7b-instruct-v0.2    | 36.45                     | 41.61                                     | 36.90                        |
| 15   | qwen-14b-chat               | 36.45                     | 41.36                                     | 34.51                        |
| 16   | qwen-7b-chat                | 27.27                     | 27.27                                     | 16.00                        |
| 17   | vicuna-13b-v1.5             | 26.26                     | 30.88                                     | 26.31                        |
| 18   | internlm-chat-20b           | 23.79                     | 26.82                                     | 25.05                        |
| 19   | wizardcoder-python-34b-v1.0 | 23.13                     | 26.45                                     | 22.40                        |
| 20   | agentlm-7b                  | 16.99                     | 20.71                                     | 17.89                        |

Table 1: Comparing the performance of LLMs as data analysis agents.

## 🔥 News

<!-- - [2023/11/29] 🔥🔥🔥 All models released at [🤗 HuggingFace](https://huggingface.co/llm-agents)! -->

## Introduction

InfiAgent-DABench is a project to build and evalute agents for advanced data analysis. Agent evaluation has been an open and challenging problem. It formulates LLMs as agents via a [REACT](https://arxiv.org/abs/2210.03629) pipeline. InfiAgent supports LLMs includinig local models (e.g., Llama) and API call (e.g.,  GPT-4). In this repo, we also build an evaluation benchmark and leaderboard to evaluate data analysis agents.


<!-- - The code for collecting data from GPT4 to train data analysis models.
- The code for training a LLM model. -->
<!-- - The **Evaluation Dataset** and **Evaluation Leadboard** to evaluate data analysis task. -->
<!-- 
## SFT Data Collection

<h1 align="center">
<img src="../../images/dataset_construction_eval.png" width="700" alt="ToRA" />
</h1>

The general collection process includes three steps, csv collection, query collection, multi-turn response data collection via InfiAgent pipeline, and a clearning step. Please follow the details in [Collection Commands](dataset_collection.md) to collect SFT data. -->
<!-- 

## LLM Training

In the fine-tuning of our model, we adopted the Vicuna format to organize the training data into a multi-turn chatbot-style arrangement, applying the FastChat training framework for implementation. Crucial hyperparameters were set, including a learning rate of 2e-5 and the employment of the AdamW optimizer paired with a cosine learning rate scheduler. For enhanced memory efficiency, we utilized Fully Sharded Data Parallelism (FSDP). The training was executed with bf16 precision and accommodated a maximum sequence length of 4096 tokens.

The training script can be found at the following script: [https://github.com/lm-sys/FastChat/blob/main/scripts/train_vicuna_7b.sh](https://github.com/lm-sys/FastChat/blob/main/scripts/train_vicuna_7b.sh). -->

<!-- There are two methods to get the  In closed-form evaluation, the model is required to generate the response in the specific way and we use the exact match to evaluate the performance.  -->


We provide an automatic evaluation for closed-form questions. In closed-form evaluation, the model is required to generated the response in the specific way and we use the exact match to evaluate the performance. Considering that most models hardly follow the format requirements, we add a reformat step after the models respond with gpt-3.5-turbo-16k which formats the responses with the format requirements. Here's a figure illustrating this process:


![](../../images/case-study-eval-data.png)
### Dataset


Our evaluation dataset includes a validation dataset and a test dataset. We only keep validation dataset for public.


The validation dataset comprises two .jsonl files, with each line representing a JSON-format dictionary containing the following keys. Additionally, a directory of CSV files for the associated questions is located under `data/`:

1. **Questions**: `data/da-dev-questions.jsonl`

- **id**: Unique identifier for each question.
- **question**: The description of the data analysis question.
- **concepts**: The concepts involved in the question.
- **constraints**: The constraints on the question that narrow down the solution into a closed-form.
- **format**: The format requirements for the output.
- **file_name**: The file name of the corresponding csv file.

2. **Labels**: `data/da-dev-labels.jsonl`

- **id**: Unique identifier for each question.
- **common_answers**: A list of labels in the format: `[[answer_name1, answer1],[answer_name2, answer2], ...]` which are corresponding to "@answer_name[answer]" in the format part of questions.

3. **Files**: `data/da-dev-tables`

### Usage

For closed-form questions, we provide an evaluation script:

```bash
python3 eval_closed_form.py \
--questions_file_path data/da-dev-questions.jsonl \
--labels_file_path data/da-dev-labels.jsonl \
--responses_file_path [YOUR_RESPONSES_FILE_PATH]
```

The responses file should adhere to the JSONL format, with each line containing a JSON dictionary that includes the 'id' and 'response' fields, formatted as follows:

```json
{"id":0, "response":"The response with @answer_name[answer] for question 0 from your model."}
{"id":1, "response":"The response with @answer_name[answer] for question 1 from your model."}
```
In addition, we provide a script for reformatting:

```bash
python3 reformat.py \
--questions_file_path data/da-dev-questions.jsonl \
--responses_file_path [YOUR_RESPONSES_FILE_PATH] \
--model [YOUR_MODEL]
```

We use an API for reformatting by default, you should put your URL for calling and api key in `url.txt` and `api_key.txt` respectively in the same directory of the script. If you want to use your own model, you need to modify the script.

<!-- 

### Metrics

For closed-form questions, we have the following metrics:

- **Accuracy Proportional by Subquestions (APSQ):**

$$
\text{APSQ} = \frac{1}{N} \sum_{i=1}^{N} \left( \frac{1}{M_i} \sum_{j=1}^{M_i} I_{ij} \right)
$$

Here, $N$ is the total number of questions, $M_i$ is the number of subquestions for the i-th question, and $I_{ij}$ is the indicator function for the j-th subquestion of the i-th question.

- **Accuracy by Questions (ABQ):**

$$
\text{ABQ} = \frac{1}{N} \sum_{i=1}^{N} \left( \prod_{j=1}^{M_i} I_{ij} \right)
$$

In this expression, the product 
\($\prod_{j=1}^{M_i} I_{ij}$\) equals 1 if all subquestions of the \(i\)-th question are answered correctly, and 0 otherwise.

- **Accuracy Uniform by Subquestions (AUSQ):**

$$
\text{AUSQ} = \frac{1}{\sum_{i=1}^{N} M_i} \sum_{i=1}^{N} \sum_{j=1}^{M_i} I_{ij}
$$

Here, the total accuracy is the sum of the values of the indicator function across all subquestions, normalized by the total number of subquestions in the dataset. -->