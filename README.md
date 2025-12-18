# BetaVAE_Disentanglement_Mini_Research
Repository for research materials, code, and analysis on β-VAE disentanglement and representation learning

## Reference - Research Papers

Here are 5 research papers relevant to β-VAE disentanglement:

1. [β-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework (2017)](https://openreview.net/pdf?id=Sy2fzU9gl)
2. [Disentangled Representations Learned from Correlated Data (Träuble et al., 2021)](https://arxiv.org/pdf/2006.07886)
3. [Understanding Disentangling in β-VAE (Burgess et al., 2018)](https://arxiv.org/pdf/1804.03599)
4. [L-VAE: Variational Auto-Encoder with Learnable Beta for Disentangled Representation (Uppal et al., 2025)](https://arxiv.org/pdf/2507.02619)
5. [AdaVAE: Adaptive β-VAE for Representation Learning (2022)](https://arxiv.org/pdf/2205.05862)


__Identified Research gaps__

## 1.Lack of Mechanisms in Handling Correlated Latent Factors in the Real-World Data
 
Most current disentanglement techniques, such as β-VAE (Higgins et al., 2017) and its extensions, make a strong assumption that generative factors in data are independent statistically. However, as identified in On Disentangled Representations Learnt from Correlated Data (Träuble et al., 2020), correlated factors frequently exist in real data, such as light and color in pictures or pose and expression in faces. Current models not only don't suppress such correlations, but they actually make them worse by bringing them to the surface in latent space, resulting in representations that are noisy and biased. While humans know to ignore this problem, there is nothing in place that can learn or suppress correlations. Most of the solutions are based on ineffective supervision or post-facto corrections that are not scalable or effective.
Gap Identified: One needs a method of disentanglement that is conscious of correlations and adaptation of learning objectives dynamically to handle interdependent variables in training, rather than after training.
 
## 2.Static β Values Constrain Adaptivity and Disentanglement Stability
 
Fixed global β value over training is used in standard β-VAE and most of the later work (Higgins et al., 2017; Burgess et al., 2018).  Though the capacity control mechanism was introduced in Understanding Disentangling in β-VAE (Burgess et al., 2018), the β value remains fixed and does not vary for all latent dimensions.  Thus, the model cannot scale to local feature correlations or differing data complexities. An adaptive β has been introduced by the recent adaptive approaches such as L-VAE (Özcan & Kalkan, 2025), which makes the model learn the best β during training time.
Yet, β is still universally learned and is not dependent on the correlations or interactions of the latent.  
Consequently, these models are unable to distinguish independent and correlated dimensions.
Gap Identified: There is currently no model that utilises per-latent or pairwise adaptive β values, which would enable the adjustment of disentanglement pressure according to factor dependencies or the intensity of correlations.

## 3.Adaptive mechanisms favoring language models.
 
AdaVAE: Exploring Adaptive GPT-2s in Variational Auto-Encoders for Language Modelling (Tu et al., 2022) is an example of how the idea of adaptivity in VAEs has recently come up in language modelling. The model has adaptive elements like Latent Attention and transformer backbones but its adaptivity is limited to how well it makes use of parameters and how attention is allocated. It can't disentangle or correlate. Additionally, it has to work with text and isn't that useful in visual or multimodal spaces. Current adaptive VAE methods in visual spaces still lack data-driven dynamic control mechanisms that condition the disentanglement process to the data structure. 
Gap Identified: Adaptive architectures have not yet been best leveraged towards correlation-conscious disentanglement of visual information, and therefore there is the opportunity to design a β-VAE that dynamically adjusts to dependencies in the data and maximizes interpretability.



## Colab Notebook

[Data set](https://www.tensorflow.org/datasets/catalog/dsprites)

The interactive **Colab notebook** for running β-VAE disentanglement example:

[Open Notebook](https://colab.research.google.com/drive/1FTKb2gMqBgCgdA3wr5ExcJG1lAi5Yqth?usp=sharing#scrollTo=5b7J9LOpMyyl)

---

## Dataset Visualization

Here’s a visual snapshot of the dataset used for the mini-lecture on β-VAE disentanglement:

![Training Loss Curve](https://github.com/NavodiSenevirathne/BetaVAE_Disentanglement_Mini_Research/blob/main/data/Training_Loss_Curve.png)

This image shows the progression of the model’s loss during training, indicating convergence and stability of the Beta-VAE optimization process.


![Original and Recunstructed Forms](https://github.com/NavodiSenevirathne/BetaVAE_Disentanglement_Mini_Research/blob/main/data/Orginal_and_Recunstructed_forms.png)

This image compares input shapes with their reconstructions, demonstrating the model’s ability to accurately reproduce the original data.


![Latent Traversal](https://github.com/NavodiSenevirathne/BetaVAE_Disentanglement_Mini_Research/blob/main/data/Latent_Traversal.png)

This image visualizes changes in generated shapes as individual latent dimensions are varied, highlighting disentanglement of underlying generative factors.


