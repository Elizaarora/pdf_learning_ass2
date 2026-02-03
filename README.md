# pdf_learning_ass2
Learning a Probability Density Function Using a Roll-Number-Based Non-Linear Transformation
📌 Project Description

This project explores the process of estimating a probability density function (PDF) from real environmental data after applying a roll-number-dependent non-linear transformation. The primary goal is to understand how statistical distributions can be learned when the original data undergoes controlled mathematical distortion.

The study uses nitrogen dioxide (NO₂) concentration measurements from an Indian air quality dataset. These values are transformed using a sinusoidal function whose parameters depend on the student’s university roll number. A Gaussian-like probability density function is then learned from the transformed data using basic statistical estimation techniques.

📂 Dataset Information

Dataset: India Air Quality Dataset

Source: Kaggle

Selected Feature: NO₂ (Nitrogen Dioxide concentration)

Nature of Data: Continuous numerical measurements

Preprocessing Performed

Before analysis, the dataset is cleaned to ensure reliable results:

Non-numeric values are removed

Missing entries are discarded

Column names are standardized for consistency

🔁 Step 1: Roll-Number-Based Non-Linear Transformation

Each original NO₂ value 
𝑥
x is converted into a transformed variable 
𝑧
z using the equation:

𝑧
=
𝑥
+
𝑎
𝑟
sin
⁡
(
𝑏
𝑟
𝑥
)
z=x+a
r
	​

sin(b
r
	​

x)

The coefficients 
𝑎
𝑟
a
r
	​

 and 
𝑏
𝑟
b
r
	​

 are uniquely determined from the roll number 
𝑟
r:

𝑎
𝑟
=
0.05
×
(
𝑟
 
m
o
d
 
7
)
a
r
	​

=0.05×(rmod7)
𝑏
𝑟
=
0.3
×
(
(
𝑟
 
m
o
d
 
5
)
+
1
)
b
r
	​

=0.3×((rmod5)+1)
Motivation for This Transformation

Introduces controlled non-linearity into the dataset

Ensures each student obtains a unique transformation

Models realistic measurement distortions found in environmental data

📐 Step 2: Learning the Probability Density Function

After applying the transformation, the distribution of the variable 
𝑧
z is modeled using a Gaussian-like probability density function:

𝑝
^
(
𝑧
)
=
𝑐
 
𝑒
−
𝜆
(
𝑧
−
𝜇
)
2
p
^
	​

(z)=ce
−λ(z−μ)
2

This formulation resembles a normal distribution and is characterized by three parameters: the mean 
𝜇
μ, the spread parameter 
𝜆
λ, and the normalization constant 
𝑐
c.

📊 Parameter Estimation Approach

The parameters of the PDF are estimated directly from the transformed data using statistical definitions.

Parameter Meaning
Symbol	Interpretation

𝜇
μ	Mean of transformed values

𝜎
2
σ
2
	Variance of transformed values

𝜆
λ	Controls distribution spread

𝑐
c	Normalization factor
Estimation Equations
𝜇
=
1
𝑛
∑
𝑖
=
1
𝑛
𝑧
𝑖
μ=
n
1
	​

i=1
∑
n
	​

z
i
	​

𝜎
2
=
1
𝑛
∑
𝑖
=
1
𝑛
(
𝑧
𝑖
−
𝜇
)
2
σ
2
=
n
1
	​

i=1
∑
n
	​

(z
i
	​

−μ)
2
𝜆
=
1
2
𝜎
2
λ=
2σ
2
1
	​

𝑐
=
1
𝜎
2
𝜋
c=
σ
2π
	​

1
	​


These values are computed programmatically after transforming the dataset.

📋 Experimental Results

The notebook calculates and displays the estimated parameters 
𝜇
μ, 
𝜆
λ, and 
𝑐
c based on the transformed NO₂ data. Since the transformation depends on the roll number, the numerical values of these parameters vary for each student.

Interpretation

𝜇
μ represents the central tendency of the transformed data

𝜆
λ determines how concentrated or spread out the PDF is

𝑐
c ensures the total probability integrates to one

📈 Visualization and Analysis

To verify the learned distribution, the following visualizations are generated:

Histogram of the transformed variable 
𝑧
z

Plot of the estimated probability density function

Overlay comparison between empirical data distribution and the learned PDF

These plots confirm that the estimated PDF provides a reasonable approximation of the transformed data distribution.

🧪 Overall Workflow

Load the air quality dataset

Extract NO₂ concentration values

Apply roll-number-dependent non-linear transformation

Compute statistical parameters

Learn the probability density function

Visualize and analyze results

🚀 Execution Instructions

Download the dataset from Kaggle

Upload the dataset to the working directory (or update the file path)

Modify the roll number in the notebook

Execute all cells sequentially

Review the estimated parameters and plots

📌 Summary

This project demonstrates how probability density functions can be estimated from real-world data after applying a structured non-linear transformation. The roll-number-based formulation ensures uniqueness, while the Gaussian-like PDF offers a simple yet effective statistical model for analysis. The approach highlights the practical connection between data preprocessing, transformation, and probabilistic modeling.

📎 References

Probability Theory and Statistical Modeling

Gaussian (Normal) Distribution

Parameter Estimation Techniques

India Air Quality Dataset (Kaggle)
