# bert_thai_sentiment
Using BERT pre-trained model to classify sentiment from Thai text

Tensorflow version = 1.15.2

## Datasets
The dataset is from Wisesight Sentiment Corpus 
https://github.com/PyThaiNLP/wisesight-sentiment

The dataset was splited into 70% training set, 20% testingset, and 10% evaluation set.  

## Labels
- 0 = Message with positive sentiment (~4,700)
- 1 = Message with negative sentiment (~6,800) 
- 2 = neu.txt Message with neutral sentiment (~14,500) 

## Training text classification
Using this command
```
!python run_classifier.py \ 
--task_name=cola \ 
--do_train=true \ 
--do_eval=true \ 
--data_dir=./data/ \
--vocab_file=./model/vocab.txt \
--bert_config_file=./model/bert_config.json \
--init_checkpoint=./model/bert_model.ckpt \
--max_seq_length=256 \
--train_batch_size=8 \
--learning_rate=2e-5 \
--num_train_epochs=3.0 \
--save_checkpoints_steps=4000 \
--output_dir=./output/ \
--do_lower_case=False
```
## Testing text classification
Using this command. You can change init_checkpoint according to the highest number in your output folder.
```
!python run_classifier.py \
--task_name=cola \
--do_predict=true \
--data_dir=./data/ \
--vocab_file=./model/vocab.txt \
--bert_config_file=./model/bert_config.json \
--init_checkpoint=./output/model.ckpt-12000 \
--max_seq_length=256 \
--output_dir=./output/
```
