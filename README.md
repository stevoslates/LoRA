# LoRA
Instruction tuning the `open_llama_3b_v2` model using[LoRA](https://arxiv.org/abs/2106.09685) (Low-Rank Adaptation).

# Notebook
Done using Google Collab, the model was traied using a NVIDIA A100 GPU.

# Model
`open_llama_3b_v2` was used from [HuggingFace](https://huggingface.co/openlm-research/open_llama_3b_v2) and is an open source reproduction of Meta AI’s LLaMA Model. I use the 3B model which has not previously been instruction tuned.

# Dataset
Using the “finance-alpaca” dataset, a financial Q&A dataset, which is a combination of [Stanford's Alpaca](https://github.com/tatsu-lab/stanford_alpaca) and [FiQA](https://sites.google.com/view/fiqa/) with another 1.3k pairs custom generated using GPT3.5. In order to instruction tune it was crucial to place the Question and Answers in a consistent format. There was no real reason for using this dataset, I just wanted to be able to learn more about fine-tuning with LLMs and Instruciton tuning is a very intersting part of this.

# LoRA Configurations
To carry out fine-tuning using the PEFT library with LoRA, I initially tried adding adapters to all linear layers in the model. However, this approach was too resource-intensive for the GPU. Therefore, I decided to focus on applying and training LoRA adapters specifically to the attention layers of the model, which include the Query, Key, Value, and Output projections. No biases are trained.
