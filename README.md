# TPU Tutorial

## Advantege of Using TPU
 * Efficiency : TPU v3-8 (the smallest TPU which has 8 cores) is faster than 8 V100 GPUs that have the same amount of memory as shown in (https://github.com/allenai/tpu_pretrain). 
 * Convient : Unlike using GPU in the school, you don't need to compete computation resources with other members, then you can start experiement any time.
 * Free : If you have Google TPU research cloud membership, it is totally free.

## Disadvantege of Using TPU
 * Not easy to use for TF 1.X and Pytorch, only easy for TF 2.X 

## How to use it freely:
 * Apply for Google TPU Research Cloud membership (I don't know the difficulty) (https://sites.research.google/trc/).
 * Perticipate in the competetion organized by Google. (I participated a Kaggle competition organized by Google in Dec 2019, after the competition, I can use TPU freely in my own research, I can still use it now).
 * Use the free TPU in Colab/Kaggle.
 * Use Google Cloud 300$ free trial (If you are new customor of Google Cloud)
 * Apply for [Google Cloud Research Credits](https://edu.google.com/programs/credits/research/?modal_active=none) (only for doctoral student).

## Code example
Actually, you can choose TF, Pytorch, and JAX/Flax for using TPU, I prefer TF 2.X, I will show some useful code example for TF 2.X and Pytorch. If you use TPU in Goolge Cloud Platform, please read the [Cloud TPU document] (https://cloud.google.com/tpu/docs) at first.

### TF 2.X
When I started to use TPU, it was the summer of 2019, I could use TPU only in TF 1.X, I just tried to run the fintuning code in BERT/XLNET official repository. I found it was really hard to use TPU at that time. Fortunatelly, at the end of 2019, TPU support for TF 2.X was realeased, it became easy to use TPU. Since TF 2.X was just released, it was unstable, I just used it in the Kaggle competiton, not in the research. This year, I found Google Reasearch have implemented many research papers using TF 2.X, I think it is the right time to use TF 2.X in the research now.

In 
