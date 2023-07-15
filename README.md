# stackgpt

Stackgpt is a (probably failed) research project in progress. The main idea is not to train whole model for n steps, but to add layers every k (where k < n and k * number_of_layers < n) steps during the training instead.

### Implementation

[nanoGPT](https://github.com/karpathy/nanoGPT) was used as the base of the stackgpt because of it's simplicity.
FLOPs were counted using the [fvcore](https://github.com/facebookresearch/fvcore) library.

### Training
All models were trained on the 2 billions tokens subset from the openwebtext dataset. The batch size during all experiments was 512 (physical batch size 16 * gradient accumulation steps 32)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkwNzA3MTQ5MF19
-->