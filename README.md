# EVOKE
[ICLR 2025 Spotlight] Uncovering Overfitting in Large Language Model Editing


## Requirements

- At least a GPU with no less than 48G memory is needed.

- For the environment, run:

```bash
conda create -n evoke python=3.9.7
pip install -r requirements.txt
```

## Running the Evaluation

An example for editing GPT-J with ROME-LTI on EVOKE dataset:

```shell
python -m experiments.evaluate_evoke_main \
    --alg_name=ROME-LTI \
    --model_name=[path/to/your/gpt-j/model] \
    --hparams_fname=gpt-j-6b.json \
    --ds_name=evoke-main \
    --num_edits=1
```

Computing the covariance matrix estimation $C$ locally is time consuming, but it will be stored after computing and can be directly used in the next run. It will then take a dozen hours to complete the editing and the evaluation.

Use `experiments.evaluate_evoke_subj_spec` to get the results on Subject Specificity task. To summarize the results, use [`experiments/summarize.py`](experiments/summarize.py):

```bash
python -m experiments.summarize --dir_name=ROME-LTI --runs=run_<run1>
```

## Acknowledgement

The code we conduct our experiments is based on [`MEMIT`](https://github.com/kmeng01/memit.git). 

For ROME and MEMIT, we use precomputed Wikipedia stats on GPT-2 XL and GPT-J from [kmeng01/rome](https://github.com/kmeng01/rome) and stats on Llama-2-7b from [mjy1111/PEAK](https://github.com/mjy1111/PEAK). Thanks to their contributions!

## Citation

If you find this work helpful for your research, please kindly cite it.

```text
@inproceedings{
    zhang2025uncovering,
    title={Uncovering Overfitting in Large Language Model Editing},
    author={Mengqi Zhang and Xiaotian Ye and Qiang Liu and Shu Wu and Pengjie Ren and Zhumin Chen},
    booktitle={The Thirteenth International Conference on Learning Representations},
    year={2025},
    url={https://openreview.net/forum?id=t8qcGXaepr}
}
```

