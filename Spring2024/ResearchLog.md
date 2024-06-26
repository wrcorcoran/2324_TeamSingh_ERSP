<!-- 
✅ - complete
⏰ - in progress
❌ - struggle / cannot complete
-->

# Spring 2024 Research Log

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#weekly-updates">Weekly Updates</a>
      <ol>
        <li><a href="#week-two">Week Two</a></li>
        <li><a href="#week-three">Week Three</a></li>
        <li><a href="#week-four">Week Four</a></li>
        <li><a href="#week-five">Week Five</a></li>
      </ol>
    </li>
  </ol>
</details>

**Key:**
✅ - complete | ⏰ - in progress | ❌ - struggle / cannot complete
<!-- Weekly Updates -->
## Weekly Updates
### Week Two
###### *Dates:* April 8-April 14, 2024

###### *Main Objective:* Compile heuristic data and compare with adversarial attacks.

#### Team Tasks:
1. Will: Build models + compile data from adversarial attacks.
2. Niyati & Wyatt: Compile previously recorded data.

#### In Progess:


#### Accomplishments:
- April 9th:
  - (Will)
    - Wasn't able to get a gpu on CNSI, so I built a GAT model for each dataset on Colab. I started working on GSage/GSaint.
    - My first time building a model that wasn't a GCN, so it took a little bit of toying around to figure out exactly what I should do. 
- April 10th:
  - (Will)
    - Today, I finally got all of the models to work. After many hours of trying to install correct dependencies, I finally got it. 
    - I made sure they are able to be called by the util function whereever necessary. They are able to be tested + all of the other features in ```util``` just like the GCN functions had.
    - Because GCNJaccard was implemented with DeepRobust, I just used that. 
    - For the others, there was a combination of copying the code from PyTorch Geometric and making it work with the infrastructure we had in place. 
- April 11th:
  - (Will)
    - Today, I started the Metaattacks. Unfortunately, I've running into a few different issues: space + cpu/gpu conversion + overall structure. 
    - I think I have the structure in place to make everything work, however, I'm out of time/focus for this at the moment. I plan to continue working over the night of Friday/Saturday morning to get the figures finalized.
- April 13th:
  - (Will)
    - Read the first four papers, here are the answers to Danish's questions from my reading:
    - As an initial note, for most of these papers it felt like I was reading a foreign language. They dealt with very niche matrix theory/neural network material I'd never seen/dealt with before. So, it's very possible that was I gleaned from these papers is incredibly shallow. However, I think I've got a decent idea of what is contained in each paper.
      - **Are there viable algorithmic or empirical methods to calculate the lipschitz constant or an upper bound on the lipschitz constant for neural networks? And are these bounds dependent on the dataset?**
        - Yes. There exists algorithmic methods for specific classes of neural networks.
        - The first is a feedforward network, as I understand it, this is one of the two most popular types of NNs. The "Compositional Estimation of Lipschitz Constants for Deep Neural Networks" paper deals explicitly with this. Here, there is an algorithm. My understanding is that given the weights of a slope-restricted FNN, iterating over each layer in the FNN, you can calculate an estimate of a Lipschitz constant by calculating the minimum "Lipschitz certificate" and doing some small massaging. This is found in section 4, remark 5.
        - Regarding a "Gaussian Random Deep Neural Network". This is dealt with in "An Analysis of the Expressiveness of Deep Neural Network Architectures Based on Their Lipschitz Constants."
          - The formula for an *upper bound* is found in Second 3.2.1, Theorem 2. It's a product over each layer and its variance along with the width of said layer. 
          - The lower bound is a conjecture, but it states that this again is a product with a very similar formula (dependent on *next* layer instead of *previous* layer). This is under *Conjecture 3* on Page 5. 
        - "UPPER AND LOWER BOUNDS FOR THE LIPSCHITZ CONSTANT OF RANDOM NEURAL NETWORKS" gives a formula for probabilistic bounds of "Deep Random ReLU Networks." Theorem 3.3 gives the formula for an upper bound which is dependent on a constant, input dimensions, and network width and depth. Likewise, it gives a similar lower bound. However, this is just 1/4 of the sqrt of the input dimensions.
  
        - No paper I read showed any indication of bounds being dependent on a dataset.
      - **Is there any work on calculating the lipschitz bounds for Graph Neural Networks? Is there a specific work that does this or are there techniques that can easily be adapted to GNNs?**
        - First, I am not aware of any ways to adapt techniques to a GNN. I understand that often ReLU functions are used in GNN models, however, I'm not sure about the convertibility between FNN/DNN models to a GNN. There's a strong possibility that the random ReLU networks have some transferibility to GNNs, which I'm not certain of. 
        - "Rethinking Propagation for Unsupervised Graph Domain Adaptation" gives a formula for calculating a Lipschitz constant based on the edge perturbation. It's given as an extremely long formula (**extremely long**). However, from what I understand this is specific to a feature extractor. This feature extractor is specific to the architecture provided in the paper (A2GNN). It's possible this metric to translate to other models which are implemented with a feature extractor. Although, I'm not sure how that works. Especially as this is focused on being given a synthetic source graph and classifying nodes in a real target graph.
      - **What is the relationship between Lipschitz constants and adversarial robustness? Which works cover this aspect and what are their findings?**
        - None of the papers I read covered this. They gave the basic intution of Lipschitz constants and the change in input affecting the change in output. However, none of them delved any deeper than this. 
    - There was a paper I found that may give more context to finding a Lipschitz constant for GNNs: [here](https://openreview.net/forum?id=USbkt99SUT&referrer=%5Bthe%20profile%20of%20Chunhui%20Zhang%5D(%2Fprofile%3Fid%3D~Chunhui_Zhang1)). I recommended Niyati read it. 
    - I've also been working to get the figures. I've exhausted my computation time on Colab, so that's not helpful. I'm still waiting for a GPU on CNSI, so until I get that, I'm kind of handcuffed. Who knew it took so much time to get a couple of figures. Luckily, I think I have everything running on the notebook, so I should be able to just open it and run once I get a pod.

#### Specific Questions:

#### Relevant Papers / Links:

#### Notes:
### Week Three
###### *Dates:* April 15-April 21, 2024

###### *Main Objective:* Compile heuristic data and compare with adversarial attacks.

#### Team Tasks:
1. Will: Build models + compile data from adversarial attacks.
2. Niyati & Wyatt: Compile previously recorded data.

#### In Progess:


#### Accomplishments:
- April 15th:
  - (Will) - Same issues as before:
    - When I run the notebooks on colab, I do not run into memory issues (however, I can't do everything on colab because there's an hour GPU limit before the runtime is disconnected.)
    - While running the notebooks on CNSI, I get a CUDA memory error after about 300 edges each time. I've tried the cache clearing/layer resizing as recommended from the PyTorch GitHub + Stack Overflow, but neither have worked. 
    - As for GSAINT and GSAGE, in order to use them with DeepRobust, I have to implement wrapper classes. That's fine, it's just going to take a long time to get everything massaged correctly. 
      - *Why is this the case?* In order to run attacks, DeepRobust requires the model to be structured like a DeepRobust model. The documentation is misleading because it says "working with PyTorch Geometric models", when in reality they are just using the DeepRobust models which are implemented on top of PyTorch Models. The Dpr2Pyg is just a conversion between datasets (i.e. if you wanted to use the preperturbed data).
    - It's been a ton of work to see no results - hopefully the other team members were able to get results from the experiments I previously ran. That would purely be data collection and wouldn't require these nasty setup problems (and the CUDA memory errors).
    - Wasn't able to get a GPU for my new environment, so I worked on getting figures for each dataset regarding the experiment. This took a few hours of massaging, but eventually, I got all of them. The images are located in the directory I've sent to the team.
- April 16th:
  - (Will) - Still no GPU for the new environment, so I switched to using Colab. 
    - I was able to build wrapper classes for DeepRobust attacks. These were for GSaint, GSage, and GAT. I've added those classes to the normal notebook folder. 
    - Likewise, I was able to construct the entire notebooks for the attack figures. I tested everything on small perturbation rates (0.025, 0.05), just to verify that the notebooks work. They do.
    - Due to Colab's random disconnections, I'm unable to use Colab to get the figures. 
    - I've spent a ton of the last week or so on this, and I need to do my classwork. I've asked the rest of the team members to get the notebooks to work on CNSI and let them run. There are no mistakes in the notebook (as it works just fine in colab), so it must be an environment thing.
- April 17th-21st:
  - Finall got all of the figures to work. Lots of debugging and time later.

#### Specific Questions:

#### Relevant Papers / Links:

#### Notes:

### Week Four
###### *Dates:* April 22-April 28, 2024

###### *Main Objective:* Compile heuristic data and compare with adversarial attacks.

#### Team Tasks:
1. Will: Build models + compile data from adversarial attacks.
2. Niyati & Wyatt: Compile previously recorded data.

#### In Progess:


#### Accomplishments:
- April 23rd:
  - (Will)
    - Today, I implemented the k-hop experiment that I'd previously been playing around with. 
    - However, it was not nearly as successful as I'd anticipated. It was dominated by the previous experiments which had been done. 
    - Rather unfortunate, because it was a lot of time spent, but didn't end up amounting to any improvement.
    

#### Specific Questions:

#### Relevant Papers / Links:

#### Notes:

### Week Five
###### *Dates:* April 29-May 5, 2024

###### *Main Objective:* Compile heuristic data and compare with adversarial attacks.

#### Team Tasks:
1. Will: Build models + compile data from adversarial attacks.
2. Niyati & Wyatt: Compile previously recorded data.

#### In Progess:


#### Accomplishments:
- May 1st:
  -  (Will): 
     -  Lots of updates:
     -  First, I looked into ways to emperically calculate a higher bound than adversarial attacks. This way to no avail. Ironically, things I expected to cause problems (like attaching a lot of low degree nodes from other classes to a single high degree nodes) caused little change. However, connecting low degree nodes to high degree nodes of the same class caused a decent amount of change (about $1/3$ that of an adversarial attack). 
     -  After talking to Danish, it doesn't seem reasonable to claim any single heuristic/adversarial attack can necessarily be an "upper" Lipschitz constant. If someone encounters a better one, then the "bound" was certainly not a bound. 
     -  After this, I had a paradigm shift that this wasn't necessarily a heuristic problem, rather, it was a matter of getting labels not to change. Changing labels is what changes the accuracy. So, I looked at ways to minimize the change in labels. There are a few functions I'll reference throughout:
        ```
        fn notInNeighborhood(i, j):
          get nodes in j's neighborhood
          verify no nodes have the same class as 
            node i

        fn allIncNeighborhood(j):
          verify all nodes in j's neighborhood are
            incorrectly classified

        fn getValidEdges(h, funcs):
          get a list of all possible edges which
            meet the following:
              - both nodes have homophily below h
              - not self loop/edge already exists
              - neither prediction is
                each other's correct class
              - all fn in funcs are true
          sort edges by lowest edge homophily
        ```
        **ALL ON TEST MASKS**
           - The first algorithm is simple:
             - getValidEdges(0.35, {})
             - add [0, ... , 30%] perturbations
             - results: change between +-0.002. 
           - Can do the **opposite** with correctly classified (set h: 1), sort by maximum edge homophily, results: between +-0.003.

          - Second algorithm: 
            - getValidEdges(1, {allIncNeighborhood})
            - add ALL edges in 5% increments (goes to 16,000 edges)
            - results: ![img](./assets/img1.png)
            - *ignore the sloppy naming / poor visualization*
          
          - Third algorithm:
            - getValidEdges(0.5, {notInNeighborhood}) 
            - get ALL edges in 5% increments (goes to ~160,000 edges)
            - results: ![img](./assets/img2.png)
          
          **NO MASK** (entire graph)
          - First algorithm:
            - getValidEdges(1, {notInNeighborhood})
            - get ALL edges in 5% increments (goes to ~160,000 edges)
            - results: ![img](./assets/img3.png)
          
          - Second algorithm:
            - getValidEdges(1, {notInNeighborhood, allIncNeighborhood})
            - get ALL edges in 5% increments (goes to ~13,000 edges)
            - results: ![img](./assets/img4.png)

        **Next steps:**
          - testing how this can be used for correctly classified (at a larger scale than just the one small example I gave) 

- May 2nd:
  - (Will):
    - Today, I worked to explore how a greedy algorithm can be used to add edges.
    - The algorithm is simple:
    ```
    fn greedy():
      add random edge (i, j)
      if change in accuracy > 0
        remove edge
      continue until budget met or edges exhausted
    ```
    - First algorithm:
      - on test mask until ptb_rate of 1
      - Notes: very easy to add. In fact, the accuracy was not changed in ANY case, so that graph is worthless. 
      - However, there is an interesting pattern. The number of iterations needed is linear in the number of edges being added (instead of exponential). For example, the slope of the linear regression model based on (ptb_rates, itr_needed) was ~1.16.
      - Here is the graph: ![img](./assets/img5.png)
    - Second:
      - repeat of above approach but with no mask. 
      - Results were very similar, however, slope was 1.33.
      - Results: ![img](./assets/img6.png)
    - Runtime of this algorithm is $O(n^2 \times \text{GNN test complexity})$, which is a drastic cut of the $O(2^{n^2})$ time needed to exhaust all possible edge combinations.
    - What are the implications of this? Not sure...possible a measure of robustness for each architecture?
    
    - As a note, I tried to add the edges which were "rejected." These edges were able to affect the accuracy of the graph at about 1/2 the rate that adversarial attacks were.

  - (Will):
    - Readings:
      - I read "AN OPTIMIZATION-BASED FRAMEWORK FOR ADVERSARIAL DEFENCE OF GRAPH NEURAL NETWORKS VIA ADAPTIVE LIPSCHITZ REGULARIZATION".
      - Here, they provided an actual calculation of the Lipschitz bounds:
      ![img](./assets/img7.png)
      - I'm yet to derive it myself to completely understand it/verify it. It uses a lot of spectral graph theory. I can give a reformed/explained version on Monday. 
      - They give analysis of adversarial attacks. Fortunately, this work corroborates our results (the graphs were almost identical).
      - They propose a new GNN model (that builds on top of another model and a denoise function), as follows:
      ![img](./assets/img8.png)
      - Although, not relevant to our use case, this model is shown to provide strength against adversarial attacks and perturbations.
  
    - Additional summaries:
      - They propose a framework, *Adaptive Lipschitz Regularization Framework*:
      - ![img](./assets/img10.png)
      - The model attempts to iterative minimize the above objective function.
      - LGNN is the loss of the GNN, LC is the lost of the noise removal function, and the rightmost side is the calculation of the Lipschitz constant with some regularization parameter gamma. 
      - ![img](./assets/img9.png)
      - Compared to other standard GCN frameworks it exhibits minimal change in accuracy and lower Lipschitz bounds. 
      - They have similar approaches for the non-convex optimization problems. 
      - ![img](./assets/img11.png)
      - Again, we can see that the model performs well in comparison to other common GNN/GCN frameworks, under different attacks. On the left is the Metattack while the right is a Netattack.

  - (Wyatt): Here are the summaries on the papers I read.
    - Adversarial Attacks on Graph Structured Data: Graph vulnerabilities have not been extensively studied, but they impact and mislead the model once trained. The researchers propose different types of attacks (modifications on the graph), trying to fool the GNN models. They show that the attacks can effectively reduce the accuracy of GNNs on both node-level and graph-level classification tasks by simply modifying the edges. It concludes showing how susceptible GNNs are to attacks the necessity for potential defenses against attacks.
    - Task and Model Agnostic Adversarial Attack on GNNs: Paper 4: Targeted Attack via Neighborhood DIStortion (TANDIS) is an adversarial attack strategy designed to be effective regardless of the specific GNN model or task being targeted, meaning the attacker doesn't need any outside information about the model. TANDIS's approach distorts the neighborhood of nodes in a graph, which significantly degrades the performance of GNNs. It uses Graph Isomorphism Networks to navigate the GNNs and quickly distort the graph. Again, it shows that we really need some defenses for our GNNs.
  - (Niyati):
    - Readings: Adversarial Training for Graph Neural Networks: Pitfalls, solutions, and New Directions
    - Goals:
      - Overcome limitations of the transductive learning setting:
        - The model has access ot the entire graph during training, including both labeled and unlabeled nodes. This can lead to biased evaluations and potentially unrealistic robustness since the model can “memorize” the graph structure
        - Authors want to avoid that
        - Focus on inductive learning setting -> Robustness becomes more realistic
      - Use flexible GNNs to adapt to adversarial attacks
      - Implement realistic adversaries for structure perturbations with both global and local constraints
        - Previous studies show global constraints werent tight allowing for unrealistic and excessive changes to the graph structure
        - Realistic adversaries
    - Section 2.1:
      - Transductive Learning setting:
        - Goal is to complete the labeling of nodes in partially labeled graph
        - The setting is often used in graph learning tasks and many benchmark datasets (Cora, Citeseer, pubmed) are designed for transductive learning
    - Theoretical Limitations:
      - Perfect Robustness Through Memorization:
        - Concept: Since the model has access to the entire graph during training, including the test nodes, it can achieve perfect robustness by memorizing the graph. This means it can remember the clean graph structure and ignore any adversarial changes at test time.
        - Defense Algorithm A: A theoretical defense algorithm could simply replace any perturbed graph with the clean graph known from training. This would result in a model that is perfectly robust because it always uses the clean graph for predictions.
        - Proposition 1: Formally, for any GNN fθfθ​, a modified model f~θf~​θ​ that always uses the clean graph can achieve perfect robustness, i.e., it will have the same predictions as fθfθ​ on the clean graph and will be unaffected by adversarial perturbations.
        - Proposition 2: This approach leads to an optimal solution for adversarial training in the transductive setting, as it minimizes the maximal misclassification rate under attack through memorization.
      - Experimental Results: Experiments show that most robustness gains are due to self-training rather than adversarial training. When self-training is removed, adversarial training alone can even hurt robustness.
      - Conclusion: use inductive learning setting where test nodes are not seen during training

    - Section 4: Adversarial Attack with Local Constraints
      - Local constraints: ensure that perturbations remain realistic and not completely disrupting the graph structure
      - Empirical evidence: experiments show that models trained without local constraints often ignore the graph structure leading to robust but less useful models
        - Models trained with local constraints maintain robustness while still leveraging the graph structure
      - LR-BCD method for generating adversarial attacks on graph structures. By incorporating both global and local constraints, LR-BCD ensures that perturbations remain realistic and do not overly disrupt the graph’s structure
      - Method is efficient and scalable, making it practical for use in adversarial training and evaluation of GNN robustness
    
    

#### Specific Questions:

#### Relevant Papers / Links:

#### Notes: