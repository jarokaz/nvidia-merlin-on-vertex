```
docker run -it --rm --gpus all --cap-add SYS_NICE \
-e AIP_MODEL_DIR='/models/t1/model' \
-e AIP_CHECKPOINT_DIR='/models/t1/checkpoints' \
-v /home/jupyter/data:/criteo_data \
-v /home/jupyter/models:/models \
gcr.io/jk-mlops-dev/hugectr-training \
python -m task \
--per_gpu_batch_size=2048 \
--model_name=deepfm_test \
--train_data=/criteo_data/criteo_processed_parquet/train/_file_list.txt \
--valid_data=/criteo_data/criteo_processed_parquet/valid/_file_list.txt \
--schema=/criteo_data/criteo_processed_parquet/train/schema.pbtxt \
--max_iter=5000 \
--max_eval_batches=200 \
--eval_batches=400 \
--dropout_rate=0.5 \
--lr=0.001 \
--num_workers=12 \
--num_epochs=0 \
--eval_interval=500 \
--display_interval=200 \
--gpus='[[0,1]]'
```

