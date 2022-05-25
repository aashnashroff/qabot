# QA and comprehension bot

The bot creates natural questions from a given a sentence or paragrap.

## Requirements
[Torch7](https://github.com/torch/torch7)

[tds](https://github.com/torch/tds)

## Paragraph-level model

	cd paragraph


### Preprocessing:

#### Generate src/target dictionary

```
th preprocess.lua -config config-preprocess
```

#### Generate embedding files (.t7)

First replace ```<path to embedding txt file>``` in ```preprocess_embedding.sh``` with real path, then run:


	./preprocess_embedding.sh

	mkdir data/embs

	cd data

	th convert.lua


### Training:

        cd ..

	th train.lua -config config-train

You can adjust the rnn size for paragraph encoder and sentence encoder by changing ```para_rnn_size``` and ```sent_rnn_size``` respectively.

### Generating:

	th translate.lua -model model/<model file name> -config config-trans

## Sample output
**Sentence:**

Oxygen is used in cellular respiration and released by photosynthesis, which uses the energy of sunlight to produce oxygen from water.

**Questions:**

– What life process produces oxygen in the
presence of light?
photosynthesis

– Photosynthesis uses which energy to form
oxygen from water?
sunlight

– From what does photosynthesis get oxygen?
water
