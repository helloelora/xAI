# Summary of "Towards unified attribution in explainable AI, data-centric AI, and mechanistic interpretability" by Zhang et al.

**The hidden unity of AI interpretability: three communities, one framework**

As AI systems grow more complex, the question "why did the model do that?" has become urgent. Researchers have been answering it from three very different angles: by looking at the input, the training data, or the model's internal components. But these communities have been working largely in isolation, reinventing similar tools with different names. This 2025 position paper argues that these three approaches share a deep technical unity, and that recognizing this unity can unlock new research directions.

### Three types of attribution, three research communities
The paper introduces three formal types of attribution.

Feature attribution: the backbone of explainable AI, asks which input features (pixels, words,...) most influenced a prediction. Data attribution, rooted in data-centric AI, asks which training examples most shaped the model's behavior. Component attribution, the heart of mechanistic interpretability, asks which internal parts of the model (neurons, attention heads, circuits) are responsible for a given output. Each gives a fundamentally different and complementary perspective on the same model.

### One toolbox to rule them all
The central claim of the paper is bold: despite their different goals, all three attribution types use the same three core techniques.

The first is perturbation. You modify something (an input feature, a training example, a neuron) and measure how the output changes. The second is gradients. You compute how sensitive the output is to small changes, without actually making those changes. The third is linear approximation. You replace the complex model locally with a simple linear one and read off the coefficients.

Methods as famous as SHAP (FA), Data Shapley (DA), and causal tracing (CA) are all just instances of perturbation applied to different objects. The difference is perspective, not technique.

### A unified family: shared concepts and shared problems
The parallels go beyond technique. Many conceptual ideas transfer cleanly across all three attribution types.

For example, the idea of smoothing through randomness appears in SmoothGrad (FA), TRAK (DA), and causal mediation analysis (CA). The idea of tracing a path appears in Integrated Gradients (FA), TracIn (DA), and path patching (CA). These are not coincidences; they reflect shared mathematical intuitions. Similarly, all three types share the same core evaluation strategies: counterfactual evaluation, task-specific evaluation, and human evaluation. And all three face the same core challenges: computational cost, inconsistency across runs, and lack of reliable evaluation benchmarks.

### The efficiency wall
Computation is a critical bottleneck for all three attribution types, and the unified view helps understand why.

Perturbation-based methods all suffer from the curse of dimensionality: there are exponentially many subsets to explore, whether of features, training points, or components. Gradient-based methods are cheaper but only first-order, meaning they can miss complex behavior. Linear approximation methods are flexible but require many model evaluations to fit well. Methods like EK-FAC have shown that gradient-based DA can scale to LLMs with 52 billion parameters, but much work remains.

### Cross-pollination as a research engine
The unified view naturally highlights gaps. Table 1 in the paper maps methods by technique and attribution type, and many cells are empty. Game-theoretic ideas have been applied broadly, but Hessian-based second-order methods are common in FA and DA but barely explored in CA. The local function approximation (LFA) framework, which unifies eight FA methods under a single mathematical umbrella, could in principle be extended to unify DA and CA methods as well.

Perhaps more importantly, using multiple attribution types together could give a much richer picture of model behavior. FA alone might not reveal that a model is relying on biased internal features; CA might catch what FA misses. A holistic analysis across all three types is the natural next step.

### Beyond interpretability: editing, steering, and regulation
The unified framework also matters beyond interpretability research itself.

Model editing (correcting a model's factual mistakes without retraining) benefits from CA to localize problems, FA to identify spurious correlations, and DA to select the right training data to guide the fix. Model steering (guiding LLM behavior toward truthfulness or harmlessness) can use CA to find the right layer, FA to find the right token, and DA to select the most informative contrastive examples. Model regulation (ensuring AI systems meet legal and ethical standards) benefits from the complementary audit that only a three-way attribution approach can provide: FA exposes input patterns, DA traces data provenance, and CA reveals architectural biases.

### A fragmented field that doesn't have to be
The authors acknowledge that the three communities have developed distinct vocabularies and practices, and that this has had real advantages. But they argue that the gains from unification now outweigh the costs. Bridges already exist: SHAP connects perturbation and linear approximation, attribution patching connects perturbation and gradients, COAR connects CA and linear approximation. Building more of these bridges is both possible and urgent. AI systems are too consequential to be understood only one piece at a time.

---

## References / Credits

- Zhang, S., Han, T., Bhalla, U., & Lakkaraju, H. (2025). *Towards unified attribution in explainable AI, data-centric AI, and mechanistic interpretability*. arXiv preprint arXiv:2501.18887.  
  Available at: [https://arxiv.org/abs/2501.18887](https://arxiv.org/abs/2501.18887)