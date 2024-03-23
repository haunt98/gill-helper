# gill-helper

## Training

```sh
# https://github.com/haunt98/gill-cc3m
cp ../gill-cc3m/processed/cc3m_train.tsv datasets/cc3m_train.tsv
cp ../gill-cc3m/processed/cc3m_val.tsv datasets/cc3m_val.tsv

mkdir -p data/cc3m/training
mkdir -p data/cc3m/validation
rm -rf data/cc3m/training/*.jpg
rm -rf data/cc3m/validation/*.jpg
cp ../gill-cc3m/output/training_01/*.jpg data/cc3m/training/
cp ../gill-cc3m/output/validation_01/*.jpg data/cc3m/validation/
```

Clone `scripts/preprocess_sd_embeddings.py` with
`sys.path.append('/path/to/gill')`

```sh
rm -rf data/cc3m/validation/clip_embs

python3 scripts/preprocess_sd_embeddings_local.py datasets/cc3m_val.tsv data/cc3m/validation/clip_embs
# Should cache after run this
```

```sh
python3 -u main.py \
    --dataset=cc3m  --val-dataset=cc3m \
    --opt-version='facebook/opt-125m' \
    --visual-model='openai/clip-vit-base-patch16' \
    --exp-name='gill_exp' \
    --log-base-dir='runs/' \
    --batch-size=2  \
    --val-batch-size=2 \
    --precision='fp32' \
    --print-freq=1 \
    --epochs=2 \
    --val_steps_per_epoch=2 \
    --steps_per_epoch=2
```
