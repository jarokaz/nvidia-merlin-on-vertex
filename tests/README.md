## Docker test environment

docker run -it --rm --gpus all \
--entrypoint /bin/bash \
-v /home/jupyter/data:/data \
-v /home/jupyter/nvidia-merlin-on-vertex/tests:/src \
nvcr.io/nvidia/merlin/merlin-training:22.02


## Preprocess data


## Run training

