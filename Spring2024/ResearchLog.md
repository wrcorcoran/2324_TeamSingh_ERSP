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

#### Specific Questions:

#### Relevant Papers / Links:

#### Notes:
