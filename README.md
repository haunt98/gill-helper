# gill-helper

## Training

```sh
# https://github.com/haunt98/gill-cc3m
cp ../gill-cc3m/processed/cc3m_train.tsv datasets/cc3m_train.tsv
cp ../gill-cc3m/processed/cc3m_val.tsv datasets/cc3m_val.tsv
```

```sh
rm -rf data/cc3m/validation/clip_embs

# Clone scripts/preprocess_sd_embeddings.py with sys.path.append('/path/to/gill')
python3 scripts/preprocess_sd_embeddings_local.py  datasets/cc3m_val.tsv data/cc3m/validation/clip_embs
```
