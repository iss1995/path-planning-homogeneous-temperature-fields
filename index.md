---
layout: default
title: Path Planning for Homogeneous Temperature Fields in Additive Manufacturing
---

# Path Planning for Homogeneous Temperature Fields in Additive Manufacturing

Welcome to our project page! We develop path planning approaches in deposition-based additive manufacturing, integrating the often overlooked process-induced temperature fields.

<div style="display: flex; justify-content: space-between; align-items: center;">
    <video width="240" height="240" controls style="margin-right: 10px;">
        <source src="./multimedia/good_pockets_2_layers.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <video width="240" height="240" controls style="margin-left: 10px;">
        <source src="./multimedia/good_pockets_2_layers.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>

## Overview
Our study addresses the critical gap in current additive manufacturing path planning methods, which tend to neglect the significant effects of temperature fields or tackle them only in limited scopes due to computational constraints. 
We introduce a novel optimization pipeline that efficiently manages large and complex geometries and does not require any data or accurate thermal model of the systems to work.

### Key Highlights
- Path planning is transformed into a sequential decision-making problem and optimized using **Monte Carlo Tree Search (MCTS)**.
- The thermal dynamics of a part are approximated with a **reduced order model (ROM)**, and the steady-state response to an arbitrary path is determined
with the **Laplace transformation**, allowing for **fast** and **accurate** evaluation of the process-induced temperature fields.
- The proposed algorithm devises paths that homogenize the temperature distribution of **complex geometries**.

## Method outline
![Pipeline](./multimedia/graphical_abstract.pdf)


Our optimization scheme seeks to discover the heating plan that deposits a layer and keeps the welding preheat temperature as constant as possible. To achieve this:
1. We start with an FVM model that simulates the deposition of a part, where new elements are activated according to a heating schedule for each layer
2. Then, the dynamics of the system are fixed at an appropriate point in time, and the system is transformed to its
reduced form, which only considers the most important aspects of its input-output behavior
3. Following this,
the Laplace transform is utilized to efficiently estimate, via the ROM, the temperature fields that would result from repeatedly applying the same heating schedule in the future
4. Leveraging this approximation,
MCTS is applied to find the heating plan that best achieves a specific goal, in this case, to minimize the standard deviation of the predicted temperature fields on the deposition layer

## Results
- **Temperature homogeneity:** Our optimization pipeline outperforms the original strategies used to deposit typical parts produced with deposition-based additive manufacturing methods.
****
<div style="text-align: center;"><strong>Initial strategies </strong></div>
<div style="display: flex; justify-content: space-between; align-items: center;">
    <!-- Column Titles -->
    <video width="240" height="240" controls style="margin-right: 10px;">
        <source src="./multimedia/bad_pockets_2_layers.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <video width="240" height="240" controls style="margin-left: 10px;">
        <source src="./multimedia/bad_dense_2layers.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>

***
<div style="text-align: center;"><strong>Optimal strategies</strong></div>
<div style="display: flex; justify-content: space-between; align-items: center;">
    <!-- Column Titles -->
    <video width="240" height="240" controls style="margin-right: 10px;">
        <source src="./multimedia/good_pockets_2_layers.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <video width="240" height="240" controls style="margin-left: 10px;">
        <source src="./multimedia/good_dense_2layers.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
</div>

***
- **Wall thickness:** The improved temperature distributions lead to improved wall-thickness consistency.
  
   ![Pipeline](./multimedia/thickness.pdf)

- **Repeatability:** The homogeneity of the fields also result in having a constant layer height throughout the layers, allowing the processes to execute seamlessly, compared to the initial strategies that fail to print because of height inconsistencies.
    ***
    ![Dense](./multimedia/group_parts_dense.pdf)
    ***
    ![Pockets](./multimedia/group_parts_pockets.pdf)
    ***
 

## Article

Check out our SSRN preprint for a detailed description of our work [here](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4656481).

## Contact

Have questions or suggestions? Feel free to reach out to us at [isideris@ethz.ch](mailto:isideris@ethz.ch).

Thank you for visiting our project page!
