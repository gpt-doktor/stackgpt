---


---

<h1 id="stackgpt">stackgpt</h1>
<p>Stackgpt is a (probably failed) research project in progress. The main idea is not to train whole model for n steps, but to add layers every k (where k &lt; n and k * number_of_layers &lt; n) steps during the training instead.</p>
<h3 id="implementation">Implementation</h3>
<p><a href="https://github.com/karpathy/nanoGPT">nanoGPT</a> was used as the base of the stackgpt because of it’s simplicity.<br>
FLOPs were counted using the <a href="https://github.com/facebookresearch/fvcore">fvcore</a> library.<br>
Also in all calculations it was assumed that 2*FLOPs(backwardpass) = FLOPs(forwardpass)</p>
<h3 id="training">Training</h3>
<p>All models were trained on the 2 billions tokens subset from the openwebtext dataset. The batch size during all experiments was 512 (physical batch size 16 * gradient accumulation steps 32).<br>
Baseline is a GPT model trained in a normal traditional way with the next characteristics: 4 layers, block size 512, embedding dimension 384, dropout 0.<br>
All of the other models were trained by adding a new layer and training for 2000 steps until model reaches 4 layers. Then training was continued without adding new layers until the number of FLOPs was equal to the baseline’s.<br>
Also I’ve tried freezing some of the layers during the training.</p>

