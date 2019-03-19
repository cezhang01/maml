# MAML (tensorflow)
This repository is (possibly the simplest) tensorflow implementation of Model Agnostic Meta Learning (MAML) by Finn et al. (https://arxiv.org/abs/1703.03400)

See https://github.com/cbfinn/maml for the original repo.

The following datasets are considered.
1. __MNIST__: 5 / 5 classes are used for training / testing, respectively. This dataset will be automatically downloaded to your directory, so you can easily verify that the code is running (without downloading from somewhere else).
2. __Omniglot__, __Mini-imagenet__: You need to download and preprocess the dataset from other sources. See ```data.py``` for some information.

After datasets are ready, just run one of the bash script files (e.g. ```bash run_mimgnet_5way1shot.sh```).

## Results
I report those accuracies after running total 60000 iterations (no early-stopping with validation set). But loss does not converge further after 30000 iterations, so you can stop training around then.

|       | mimgnet-5way1shot| mimgnet-5way5shot | omniglot-20way1shot| omniglot-5way1shot |
| ------| ---------------- | ----------------- | ------------------ | ------------------- |
| Paper (first order approx.) | 48.07            | 63.15             | 95.8               | 98.7                |
| Ours (first order approx.)  | __48.67__        | __xx.xx__         | __xx.x__           | __xx.x__            |

## Caution
1. Different initializers for the weights are used (see ```model.py```). I couldn't successfully reproduce the results with the one used in the original repo.
2. Meta- learning rate is set to ```1e-4```. I found that ```1e-3``` is too large, especially for the 1-shot cases. Multiple users have reported the difficulty of training MAML, so I strongly believe that the correct learning rate should be lower than that.
