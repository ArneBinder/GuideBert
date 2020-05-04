# log


## 2020-05-04
* rebase transformers fork
* use [new train script](https://github.com/ArneBinder/transformers/blob/c81152600452ad1bec4ab705356788d29a3573ee/examples/run_language_modeling.py)
* use tau according to [gumble-softmax paper](https://arxiv.org/pdf/1611.01144.pdf)
* start run `@server=dfki-gpu9` `@screen=guidebert2`:
```
CUDA_VISIBLE_DEVICES=2 python run_language_modeling.py --output_dir=output/mlm/guidebert_tau --model_type=guidebert --model_name_or_path=guidebert-albert-base-v2 --do_train --train_data_file=data/wikitext/wikitext-2-raw/wiki.train.raw --do_eval --eval_data_file=data/wikitext/wikitext-2-raw/wiki.valid.raw --mlm --overwrite_output_dir --num_train_epochs 100 --save_total_limit 5 --logging_steps 100 --logging_first_step --per_gpu_train_batch_size 4 --gradient_accumulation_steps 2
```
