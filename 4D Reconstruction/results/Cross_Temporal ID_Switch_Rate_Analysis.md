## Cross-Temporal ID-Switch Rate Analysis

To evaluate temporal identity consistency in reconstructed 4D scenes, we analyze the **cross-temporal ID-Switch Rate**. This metric measures how frequently the identity assigned to the same physical object changes incorrectly across time.

An ID switch occurs when an object assigned identity (ID_i) at one timestamp is incorrectly assigned another identity (ID_j) at a later timestamp, even though both observations correspond to the same physical object. A lower ID-Switch Rate therefore indicates more reliable temporal association and stronger object-level consistency.

The metric is calculated as:

[
\text{ID-Switch Rate} =
\frac{N_{\mathrm{switch}}}
{N_{\mathrm{association}}}
\times 100%,
]

where:

* (N_{\mathrm{switch}}) denotes the number of incorrect identity transitions observed across time.
* (N_{\mathrm{association}}) denotes the total number of valid cross-temporal object associations.
* A lower value indicates better temporal identity consistency.

For example, if 65 incorrect identity transitions occur among 1,000 valid cross-temporal associations, the resulting ID-Switch Rate is (6.5%).

---

## 1. ID-Switch Rate Distribution

<p align="center">
  <img src="./ID-Switch%20Rate_box_plot.png" width="70%">
</p>

<p align="center">
  <b>Figure 5.</b> Cross-temporal ID-Switch Rate distribution across 30 reconstructed 4D scenes.
</p>

Figure 5 presents the distribution of cross-temporal ID-Switch Rates across six evaluated methods using a box plot. Each distribution summarizes the results obtained from 30 reconstructed 4D scenes and shows the median, interquartile range, overall variation, and potential outlier cases.

Our method achieves the **lowest median ID-Switch Rate of approximately 6.4%**, with an overall ID-Switch Rate of approximately **6.5%**. The compact interquartile range indicates that the proposed method maintains stable identity associations across different dynamic scenes.

In contrast, the baseline methods exhibit:

* Higher median ID-Switch Rates
* Larger interquartile ranges
* Greater variation across reconstructed scenes
* More frequent high-error or outlier cases

Among the baseline methods, ARM4R and ManiGaussian achieve relatively lower ID-Switch Rates than the other competing approaches. Their median errors, however, remain considerably higher than those of the proposed method.

C2FARM-BC, LLARVA, and PerAct show larger distributions and higher upper ranges, indicating increased sensitivity to scene dynamics, object interactions, and temporal ambiguity. LLARVA exhibits the highest median ID-Switch Rate and several large-error cases, suggesting difficulty in maintaining persistent object identities over long temporal sequences.

The low median and compact distribution achieved by our method demonstrate that the improvement is not limited to a small subset of scenes. The proposed approach maintains consistent temporal identity association across a diverse set of 4D reconstruction scenarios.

---

## 2. Scene-Condition Interaction Analysis

<p align="center">
  <img src="./ID-Switch%20Rate_interaction_plot.png" width="70%">
</p>

<p align="center">
  <b>Figure 6.</b> Mean cross-temporal ID-Switch Rates with 95% confidence intervals under different scene conditions.
</p>

Figure 6 compares the mean ID-Switch Rates of the six evaluated methods under five representative dynamic-scene conditions:

* Regular Motion
* Fast Motion
* Partial Occlusion
* Object Crossing
* Re-entry

Each point represents the mean ID-Switch Rate under the corresponding condition, while the error bars indicate the **95% confidence interval**. Lower values represent better temporal identity consistency.

Our method consistently achieves the lowest ID-Switch Rate across all evaluated conditions. The lowest error is observed under regular object motion, where consecutive observations provide stable geometric and appearance information for temporal association.

The ID-Switch Rate increases under fast motion because larger object displacement between timestamps reduces spatial overlap and makes temporal matching more difficult. Partial occlusion further increases association ambiguity because only a portion of the object remains visible.

Object Crossing represents the most challenging condition for nearly all evaluated methods. When multiple objects move close to or across one another, their spatial locations and visual appearances may become temporarily ambiguous, increasing the probability of incorrect identity reassignment.

Re-entry also produces a higher ID-Switch Rate than regular motion. When an object leaves the observed region and later reappears, the model must reconnect the new observation to its previous identity rather than assigning a new identity.

Despite these challenges, the proposed method maintains substantially lower ID-Switch Rates than all competing methods. The relatively narrow confidence intervals also indicate stable performance across scenes belonging to the same condition.

---

## 3. Discussion

The cross-temporal ID-Switch analysis reveals several important characteristics of the proposed 4D reconstruction framework.

### Temporal Identity Consistency

The overall ID-Switch Rate of **6.5%** and median rate of approximately **6.4%** demonstrate that the proposed method preserves object identities across most valid temporal associations.

This result confirms that the reconstructed 4D representation maintains persistent object-level information rather than independently reconstructing each timestamp without temporal correspondence.

### Stability across 4D Scenes

The compact box-plot distribution indicates that the proposed method performs consistently across the 30 evaluated scenes. The improvement is therefore not driven by a small number of simple sequences.

Reduced variation is particularly important for real-world deployment because unstable temporal association can fragment object trajectories or incorrectly merge the motion histories of different objects.

### Robustness to Challenging Conditions

The interaction analysis shows that fast motion, partial occlusion, object crossing, and object re-entry increase the difficulty of temporal identity association.

Our method retains a clear performance advantage under all five conditions. This suggests that the proposed representation effectively combines temporal, spatial, geometric, and appearance information when associating objects across time.

### Reduced Identity Fragmentation

A lower ID-Switch Rate reduces the probability that one physical object will be reconstructed as multiple independent identities. It also reduces the risk of assigning observations from different objects to the same temporal trajectory.

This improves the integrity of reconstructed object trajectories, motion histories, and temporal relationships within the 4D scene.

### Effectiveness of Temporal 4D Representation

The results validate the effectiveness of explicitly incorporating temporal information into the scene representation. By modeling object evolution and cross-temporal correspondence, the proposed framework provides more reliable dynamic-scene understanding than approaches that primarily depend on local frame-to-frame matching.

The remaining errors are concentrated in highly ambiguous situations, particularly object crossing, prolonged occlusion, and re-entry after disappearance. These conditions represent the primary opportunities for future improvement through long-term object memory, trajectory constraints, and object re-identification mechanisms.

---

## 4. Summary

Overall, the proposed method achieves an overall cross-temporal ID-Switch Rate of **6.5%**, with a median value of approximately **6.4%** across 30 reconstructed 4D scenes.

The box-plot analysis demonstrates lower error and reduced variability compared with all evaluated baseline methods. The scene-condition interaction analysis further shows that the proposed method consistently maintains the lowest ID-Switch Rate under regular motion, fast motion, partial occlusion, object crossing, and object re-entry.

These results demonstrate that the proposed 4D reconstruction framework provides reliable temporal identity preservation and robust object-level association across dynamic environments. This capability supports downstream applications that require persistent scene understanding, including object trajectory analysis, robotic interaction, motion prediction, and long-term environment monitoring.
