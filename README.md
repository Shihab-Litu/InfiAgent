<h1 align="center">
<img src="images/infiagent_logo.png" width="100" alt="ToRA" />
<br>
InfiAgent: An Open-Source Agent Framework
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
<!--  -->


This is the repo for the InfiAgent project. InfiAgent aims to support building an agent demo from scratch, supporting code execution, API call, batch inference, and sandbox mangagement. You can easily build your own agents based on InfiAgent. 




## 🔥  News
- [2024/2/21] InfiAgent-DABench and DA-Agent released at [huggingface](https://huggingface.co/infiagent).
- [2024/1/27] [DAEval](https://github.com/InfiAgent/InfiAgent/tree/main/examples/DA-Agent) with human filtering updated.
- [2024/1/10] Our paper on InfiAgent-DABench released on [arxiv](https://arxiv.org/abs/2401.05507).
- [2023/12/15] [InfiAgent-DABench](https://github.com/InfiAgent/InfiAgent/tree/main/examples/DA-Agent) released.
- [2023/11/29] InfiAgent repo, and website released.


## Framework Features

InfiAgent is a project for building your own agents via code execution and API call. It formulates LLMs as agents via a [REACT](https://arxiv.org/abs/2210.03629) pipeline by default. You also can define your own prompt templates.



We have provided a comprehensive pipeline code for running your agent locally. Within the pipeline, we offer API calls, local model inference, a Python code sandbox based on Docker, and a frontend built on Streamlit. We take GPT-3.5 as an example to show how to build a data anaylsis agent given a LLM interface.


1. **API Calls:**

   Simply fill in your API Key, and you can begin making calls to models such as GPT-3.5, GPT-4, Claud, and more to run your code interpreter pipeline.
3. **Local Model Inference:**

   If you would like to run models locally, we've incorporated the capability to perform local inference on your Nvidia GPU. The local inference feature is implemented based on vLLM for optimized performance on your local machine.
5. **Python Code Sandbox:**

   To execute Python code, we implement a Python code sandbox using a subprocess, which is convenient but may introduce certain security issues. 

   Also, we have implemented a Python code sandbox based on Docker, where you can run the pipeline executing the code generated by LLM in an isolated environment without worrying about damage to local files.

   Considering the complexity of the Docker environment configuration, we have set running the sandbox using subprocess as the default option.
7. **Streamlit-based Frontend:**

   We have provided a front-end based on Streamlit, allowing you to interact with the pipeline in a visualized manner for a clearer and simpler experience.

# Usage

## Installation

InfiAgent requires **Python version >= 3.9**.

1. Install infiagent and requirements
```
pip install .
```

2. You can easily use the following command to start a demo using APIs. You can changes the config s if you need. 
```bash
# Supported LLM: OPEN_AI, AZURE_OPEN_AI, LLAMA, OPT
# api_key is required for API-based models
bash run_demo.sh --llm OPEN_AI --api_key <YOUR API KEY> --config_path configs/agent_configs/react_agent_gpt4_async.yaml
```

3. (Optional) Using docker python sandbox
```bash
docker build -t codesandbox .
bash run_demo.sh --llm OPEN_AI --api_key <YOUR API KEY> --config_path configs/agent_configs/react_agent_gpt4_async_docker.yaml
```



```bash
pip3 install vllm
```
## Demo Usage



## Run your local model serving

1. Our local LLM service is developed on vLLM. First, You should install by command:
   
```
pip install vllm fschat
```
1.  you can start a vLLM model serving by running this command:


```bash
python3 ./activities/vllm_api_server.py --model "meta-llama/Llama-2-7b-hf"  --served_model_name "meta-llama/Llama-2-7b-hf"
```
At this point, we only support Linux environment.

3. You can try this command if the serving is successfully starting:

```bash
curl http://localhost:8000/v1/completions \
      -H "Content-Type: application/json" \
      -d '{
         "model": "meta-llama/Llama-2-7b-hf",
         "prompt": "San Francisco is a",
         "max_tokens": 7,
         "temperature": 0
      }'
```

4. Then you can run the demo by this command with your local model:

```bash
bash run_demo.sh --llm "meta-llama/Llama-2-7b-hf" --config_path configs/agent_configs/react_agent_llama_async.yaml
```

If you run in worker, please change `openai.api_base` in the `./src/infiagent/llm/client/llama.py` to your podIP and then run `pip install .`

For example, you can change the setting from `"http://localhost:8000/v1"` to `"http://[fdbd:dc03:9:130:5500::e5]:8000/v1"`.



## Acknowledge

We would like to express our sincere gratitude to the following open-source projects for their invaluable assistance to our project：

 - [vLLM](https://github.com/vllm-project/vllm)
 - [FastChat](https://github.com/lm-sys/FastChat)
 - [Gentopia](https://github.com/Gentopia-AI/Gentopia)
 - [autogen](https://github.com/microsoft/autogen)



## Contact

If you have any questions, feedback, or would like to collaborate on this project, please feel free to reach out to us through huxueyu@zju.edu.cn. Your inquiries and suggestions are highly appreciated. 

Thank you for your interest in our work!



## Citation

If you find our repo useful, please kindly consider citing:

```
@misc{hu2024infiagentdabench,
      title={InfiAgent-DABench: Evaluating Agents on Data Analysis Tasks}, 
      author={Xueyu Hu and Ziyu Zhao and Shuang Wei and Ziwei Chai and Qianli Ma and Guoyin Wang and Xuwu Wang and Jing Su and Jingjing Xu and Ming Zhu and Yao Cheng and Jianbo Yuan and Jiwei Li and Kun Kuang and Yang Yang and Hongxia Yang and Fei Wu},
      year={2024},
      eprint={2401.05507},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

