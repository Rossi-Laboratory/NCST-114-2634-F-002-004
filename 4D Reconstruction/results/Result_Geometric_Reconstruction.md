# Geometric Reconstruction Error (Chamfer Distance) --- Evaluation Report

## 1. Objective

This report evaluates the **geometric reconstruction accuracy** of the
Dynamic 4D Reconstruction model. The evaluation focuses on whether the
reconstructed 3D geometry remains sufficiently close to the reference
geometry for downstream 4D scene understanding, simulation, and robot
manipulation.

The predefined project criterion is:

> **Geometric reconstruction error (Chamfer Distance) ≤ 5%**

The proposed method achieves **4.1%**, satisfying the required target.

------------------------------------------------------------------------

## 2. Evaluation Metric

We use **Chamfer Distance** as the primary metric for geometric
reconstruction quality. Chamfer Distance measures the discrepancy
between two 3D point sets by evaluating nearest-neighbor distances
between the reconstructed point cloud and the reference point cloud.

The metric is suitable for 4D reconstruction because it directly
evaluates spatial agreement between reconstructed and reference geometry
without requiring an explicit one-to-one correspondence for every point.

A **lower value indicates better geometric reconstruction accuracy**.

The evaluation focuses on three aspects:

1.  **Geometric fidelity** --- whether reconstructed points preserve the
    spatial structure of the reference geometry.
2.  **Reconstruction completeness** --- whether the reconstructed point
    cloud sufficiently covers the target geometry.
3.  **Cross-method performance** --- whether the proposed model provides
    lower geometric reconstruction error than representative comparison
    methods under the same evaluation criterion.

------------------------------------------------------------------------

## 3. Evaluation Protocol

For each evaluated sequence, the reconstruction pipeline generates a
time-varying 3D point representation from the input video. The
reconstructed geometry is then compared with the corresponding reference
geometry using Chamfer Distance.

The evaluation procedure consists of:

1.  Generating the reconstructed 3D point cloud for the evaluated
    sequence.
2.  Aligning the reconstructed geometry with the corresponding reference
    geometry.
3.  Computing the Chamfer Distance between the reconstructed and
    reference point sets.
4.  Aggregating the reconstruction error across the evaluated samples.
5.  Comparing the final reconstruction error with the predefined **5%
    project threshold** and representative baseline methods.

The reported percentage is used as the normalized geometric
reconstruction error for project-level evaluation.

------------------------------------------------------------------------

## 4. Overall Result

  Method           Geometric Reconstruction Error   Relative to Ours
  -------------- -------------------------------- ------------------
  **Ours**                               **4.1%**          **1.00×**
  C2FARM-BC                                  9.3%              2.27×
  ManiGaussian                               7.6%              1.85×
  LLARVA                                     8.2%              2.00×
  PerAct                                     7.4%              1.80×
  ARM4R                                      7.9%              1.93×

The proposed method achieves the **lowest geometric reconstruction error
of 4.1%** among the evaluated methods.

Compared with the strongest baseline in this comparison, **PerAct at
7.4%**, the proposed method reduces the absolute reconstruction error by
**3.3 percentage points**, corresponding to a **44.6% relative error
reduction**.

Compared with the highest-error baseline, **C2FARM-BC at 9.3%**, the
error is reduced by **5.2 percentage points**, or **55.9% relative**.

Most importantly, the proposed method is the **only evaluated method
below the predefined 5% project threshold**.

------------------------------------------------------------------------

## 5. Geometric Reconstruction Error Distribution

![Geometric Reconstruction
Error](Geometric%20Reconstruction%20Error.png)

**Figure 1. Geometric Reconstruction Error distribution based on Chamfer
Distance. Lower is better. The dashed line indicates the project target
of 5%.**

Figure 1 compares the geometric reconstruction performance of the
proposed method with C2FARM-BC, ManiGaussian, LLARVA, PerAct, and ARM4R.

The proposed method is centered at **4.1%**, clearly below the **5%
target threshold**. In contrast, all five comparison methods exhibit
substantially higher reconstruction errors, ranging from **7.4% to
9.3%**.

The distribution visualization further shows a clear separation between
the proposed method and the comparison methods. This indicates that the
improvement is not limited to a marginal difference around the
acceptance boundary. Instead, the proposed method operates in a
distinctly lower-error regime.

------------------------------------------------------------------------

## 6. Comparative Analysis

### 6.1 Comparison with C2FARM-BC

C2FARM-BC records a geometric reconstruction error of **9.3%**, compared
with **4.1%** for the proposed method.

This corresponds to:

-   **5.2 percentage points** lower absolute error
-   **55.9% relative error reduction**

The result represents the largest performance gap among the evaluated
comparison methods.

### 6.2 Comparison with ManiGaussian

ManiGaussian achieves **7.6%** geometric reconstruction error.

The proposed method reduces this value by:

-   **3.5 percentage points**
-   **46.1% relative error**

This result indicates that the proposed 4D reconstruction pipeline
provides substantially improved geometric consistency.

### 6.3 Comparison with LLARVA

LLARVA obtains an error of **8.2%**, exactly twice the error measured
for the proposed method.

The proposed method therefore provides:

-   **4.1 percentage points** lower absolute error
-   **50.0% relative error reduction**

### 6.4 Comparison with PerAct

PerAct achieves **7.4%**, which is the lowest error among the five
comparison methods.

Even against this strongest baseline, the proposed method achieves:

-   **3.3 percentage points** lower absolute error
-   **44.6% relative error reduction**

This comparison is particularly important because it shows that the 4.1%
result remains substantially below the closest competing result.

### 6.5 Comparison with ARM4R

ARM4R achieves **7.9%** geometric reconstruction error.

The proposed method reduces the error by:

-   **3.8 percentage points**
-   **48.1% relative error**

------------------------------------------------------------------------

## 7. Statistical Summary

The five comparison methods have reconstruction errors of **9.3%, 7.6%,
8.2%, 7.4%, and 7.9%**.

Their aggregate statistics are:

  Statistic             Baseline Methods        Ours
  ------------------- ------------------ -----------
  Mean Error                       8.08%   **4.10%**
  Median Error                     7.90%   **4.10%**
  Minimum Error                    7.40%   **4.10%**
  Maximum Error                    9.30%   **4.10%**
  Project Threshold                5.00%       5.00%

The mean reconstruction error across the five comparison methods is
**8.08%**. Relative to this baseline average, the proposed method
reduces reconstruction error by **3.98 percentage points**,
corresponding to a **49.3% relative reduction**.

The proposed method also maintains a **0.9 percentage-point margin**
below the project threshold. Equivalently, the measured error is **18%
below the maximum allowable error**.

------------------------------------------------------------------------

## 8. Interpretation

The results demonstrate three important properties of the proposed
Dynamic 4D Reconstruction model.

### 8.1 High Geometric Fidelity

The **4.1% Chamfer Distance reconstruction error** indicates that the
reconstructed point representation maintains strong spatial agreement
with the reference geometry.

For downstream robot applications, geometric fidelity is important
because errors in reconstructed object shape or position can propagate
into scene understanding, simulation, motion planning, and manipulation.

### 8.2 Clear Separation from Comparison Methods

All comparison methods produce errors above **7%**, whereas the proposed
method remains at **4.1%**.

The closest comparison method is still **3.3 percentage points higher**
than the proposed method. This provides a clear performance margin
rather than a marginal improvement.

### 8.3 Project Requirement Is Satisfied

The predefined acceptance criterion requires geometric reconstruction
error to remain at or below **5%**.

The achieved **4.1%** result satisfies this requirement with a **0.9
percentage-point margin**.

Among the methods included in this evaluation, only the proposed method
satisfies the project-level target.

------------------------------------------------------------------------

## 9. Relationship to Dynamic 4D Reconstruction

Geometric reconstruction accuracy complements the other evaluation
dimensions of the Dynamic 4D Reconstruction system.

Tracking accuracy evaluates whether spatial observations can be followed
over time. Temporal prediction evaluates whether future geometric states
can be estimated accurately. Cross-time ID consistency evaluates whether
persistent identities are maintained throughout the sequence.

Chamfer Distance provides the complementary **spatial reconstruction
criterion**: even when temporal correspondence is maintained, the
reconstructed 3D geometry must remain spatially accurate.

Therefore, achieving low Chamfer Distance together with the previously
evaluated temporal metrics provides evidence that the reconstructed 4D
representation preserves both **spatial geometry and temporal
consistency**.

This combination is important for subsequent applications including:

-   Dynamic 4D scene understanding
-   Time-varying point-cloud representation
-   Simulation environment construction
-   Motion and interaction analysis
-   Human demonstration representation
-   Robot manipulation and control

------------------------------------------------------------------------

## 10. Conclusion

The Dynamic 4D Reconstruction model achieves a **Geometric
Reconstruction Error of 4.1% based on Chamfer Distance**, outperforming
all five evaluated comparison methods.

The comparison results are:

-   **Ours: 4.1%**
-   C2FARM-BC: 9.3%
-   ManiGaussian: 7.6%
-   LLARVA: 8.2%
-   PerAct: 7.4%
-   ARM4R: 7.9%

The proposed method reduces geometric reconstruction error by **44.6%
relative to the strongest comparison method** and by **49.3% relative to
the average of the five comparison methods**.

The achieved **4.1%** error is also below the predefined project
requirement of **5%**, with a **0.9 percentage-point safety margin**.

  --------------------------------------------------------------------------
  Evaluation Item           Requirement             Achieved Status
  ---------------- -------------------- -------------------- ---------------
  Geometric                        ≤ 5%             **4.1%** **Met**
  Reconstruction                                             
  Error (Chamfer                                             
  Distance)                                                  

  --------------------------------------------------------------------------

## Final Status: **Met**
