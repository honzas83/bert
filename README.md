# BERT with SentencePiece support 

## Sentence Piece support

Use https://github.com/google/sentencepiece to generate a SPM model, then, you can use the modified `create_pretraining_data.py` script
and supply the `--piece=sentence` and `--piece-model=SPM_model_filename` parameters.

Example:

```shell
python create_pretraining_data.py \
  --input_file=${TXT} \
  --output_file=${TXT%.txt}${SUFFIX}.tfrecord \
  --vocab_file=${VOCAB} \
  --piece=sentence \
  --piece_model=${PIECE_MODEL} \
  --do_lower_case=False \
  --do_whole_word_mask=True \
  --do_lower_case=True \
  --max_seq_length=128 \
  --max_predictions_per_seq=20 \
  --masked_lm_prob=0.15 \
  --random_seed=12345 \
  --dupe_factor=5
```

The rest of the BERT pipeline is the same as in https://github.com/google-research/bert .
