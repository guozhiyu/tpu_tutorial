# TPU Tutorial

## Advantage of Using TPU
 * Efficiency: TPU v3-8 (the smallest TPU which has 8 cores, 16GB*8) is faster than 8 V100 GPUs that have the same amount of memory as shown in (https://github.com/allenai/tpu_pretrain). 
 * Convenient: Unlike using GPU in the school, you don't need to compete for computation resources with other members, then you can start the experiment any time.
 * Free: If you have Google TPU research cloud membership, it is totally free.

## Disadvantage of Using TPU
 * Not easy to use for TF 1.X and Pytorch, only easy for TF 2.X, I don't know about JAX/Flax.

## How to use it freely:
I find there are five feasible ways:
 * Apply for Google TPU Research Cloud membership (I don't know the difficulty) (https://sites.research.google/trc/).
 * (Highly recommended) Participate in the competition organized by Google. (I participated in a Kaggle competition organized by Google in Dec 2019, after the competition, I can use TPU freely in my own research, I can still use it now, I can run up to 5 TPU-v3 at the same time).
 * Use the free TPU in Colab/Kaggle notebook.
 * Use Google Cloud 300$ free trial (If you are a new customer of Google Cloud)
 * Apply for [Google Cloud Research Credits](https://edu.google.com/programs/credits/research/?modal_active=none) (1000$ GCP credits, only for doctoral students).

## Code example
Actually, you can choose TF, Pytorch, and JAX/Flax for using TPU, I prefer TF 2.X, I will show some useful code examples for TF 2.X and Pytorch. If you use TPU in Google Cloud Platform, please read the [Cloud TPU document](https://cloud.google.com/tpu/docs) at first. It is highly recommended to use the newly released [TPU Virtual Machine](https://cloud.google.com/blog/products/compute/introducing-cloud-tpu-vms).

### TF 2.X
When I started to use TPU, it was the summer of 2019, I could use TPU only in TF 1.X, I just tried to run the fine-tuning code in BERT/XLNET official repository. I found it was really hard to use TPU in TF 1.X. Fortunately, at the end of 2019, TPU support for TF 2.X was released, it became easy to use TPU. Since TF 2.X was just released, it was unstable, I just used it in the Kaggle competition, not in the research. This year, I find Google Research has implemented many research papers using TF 2.X, I think it is the right time to use TF 2.X in the research now.

In TF 2.X, the simplest way to for using TPU is using the `model.fit() ` in the training process. You can also write your custom training loop. Here are some useful examples:
 * `model.fit()`:(https://www.tensorflow.org/text/tutorials/bert_glue), (https://github.com/huggingface/transformers/blob/master/examples/tensorflow/text-classification/run_glue.py)
 * Custom training loop: (https://github.com/tensorflow/models/blob/e3c7e300866dcb7d1ff020c18daababbdc232711/official/nlp/bert/model_training_utils.py), it is  used in (https://github.com/tensorflow/models/blob/e3c7e300866dcb7d1ff020c18daababbdc232711/official/nlp/bert/run_squad_helper.py)

When using TPU in TF 2.X, please keep in mind that:
 * Every input sequence should be the same length.
 * Don't use `tf.keras.layers.Embedding`, please refer to [HuggingFace TFBertEmbeddings](https://github.com/huggingface/transformers/blob/master/src/transformers/models/bert/modeling_tf_bert.py#L132).

Some papers of Google Research that have used TPU in TF 2.X:
 * [Colorization Transformer](https://github.com/google-research/google-research/tree/master/coltran)
 * [On the Transformer Growth for Progressive BERT Training](https://github.com/google-research/google-research/tree/master/grow_bert)
 * [Big Bird: Transformers for Longer Sequences](https://github.com/google-research/bigbird).
### Pytorch
You can use TPU by [torch_xla package](https://github.com/pytorch/xla) or [accelerate](https://huggingface.co/docs/accelerate/):
* torch_xla: All examples in [Huggingface Pytorch examples](https://github.com/huggingface/transformers/tree/master/examples/pytorch) without suffix `no_trainer`, such as `run_glue.py`.
* accelerate: All examples in [Huggingface Pytorch examples](https://github.com/huggingface/transformers/tree/master/examples/pytorch) with suffix `no_trainer`, such as `run_glue_no_trainer.py`

Also, in Pytorch, every input sequence should be the same length. 

###  JAX/Flax
I am studying it now, I find many researchers in Google and HuggingFace are using it. HuggingFace also has some [examples](https://github.com/huggingface/transformers/tree/master/examples/flax) about it.


