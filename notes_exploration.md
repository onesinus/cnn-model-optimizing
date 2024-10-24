
–
and thus have weight matrices which just have two possible values 0 or 1, and the quantization function there is simply the sign(𝑥) function (assuming the weights are symmetrically distributed around 0).
The promise with such extreme quantization approaches is the theoretical 32/1 = 32× reduction
in model size without much quality loss.

Kayaknya boleh juga nih di explore: binary quantization, apakah cocok dengan use case digit recognition? Kalau bisa pake ubah fungsi aktivasi nya atau teknik quantificationnya jadi binary, bisa save banyak nih…
https://medium.com/tensorflow/tensorflow-model-optimization-toolkit-post-training-integer-quantization-b4964a1ea9ba 

Compared to quantization-aware training, this tool is much simpler to use, and offers comparable accuracy on most models. There may still be use cases where quantization-aware training is required, but we expect this to be rare as we continue to improve post-training tooling.
In summary, a user should use “hybrid” post training quantization when targeting simple CPU size and latency improvements. When targeting greater CPU improvements or fixed-point accelerators, they should use this integer post training quantization tool, potentially using quantization-aware training if accuracy of a model suffers.


– 
Vanhoucke et al. [153] demonstrated a 3× inference speedup using a fully fixed-point model on an x86 CPU, when compared to a floating-point model on the same CPU, without sacrificing accuracy. The weights are still quantized similar to post-training quantization, however all layer inputs (except the first layer) and the activations are fixed-point


Can mix distillation also?

Adalagi loh yang lain, seperti Low Rank Matrix Factorization, K-Means Clustering (tapi sepertinya tidak perlu cover semua, ini kemungkinan di skip aja dulu)

For performance reasons, it is best to consider the common operations that follow a typical
layer such as Batch-Norm, Activation, etc. and ‘fold’ them in the quantization operations
