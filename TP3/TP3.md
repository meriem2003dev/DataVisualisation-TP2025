# Practical Work: Exploratory Data Analysis (EDA) on Metro Interstate Traffic Volume

**Objective:** Apply the principles of Exploratory Data Analysis (EDA) to a real-world dataset to discover patterns, check assumptions, and visualize key statistical relationships.

**Tools:** Python (Pandas, NumPy, Matplotlib/Seaborn, optionally Plotly/Altair)

## I. Setup and Data

## 1.1. Dataset Introduction

We will use the **Metro Interstate Traffic Volume Dataset** from the UCI Machine Learning Repository. This dataset captures hourly traffic volume on the I-94 Westbound route in the Minnesota metro area, along with various contextual and environmental factors.

#### Key Variables

| Variable | Type | Description |
|----------|------|-------------|
| `traffic_volume` | Numerical (Target) | The number of cars per hour. |
| `temp` | Numerical | Temperature in Kelvin. |
| `rain_1h` / `snow_1h` | Numerical | Amount of rain/snow in the last hour. |
| `clouds_all` | Numerical | Percentage of cloud cover. |
| `weather_main` | Categorical | Short description of weather (e.g., 'Clouds', 'Clear', 'Rain'). |
| `holiday` | Categorical | Indicates if the day is a named holiday. |
| `date_time` | Date/Time | The timestamp for the hourly record. |

#### Setup Task:

- Download the dataset or load it directly from the UCI source if possible.
- Load the data into a Pandas DataFrame.
- Perform an initial inspection using `df.head()`, `df.info()`, and `df.describe(include='all')`.

### 1.2. Exploration Techniques Applied

In this lab, you will demonstrate both **Graphical** and **Non-Graphical EDA** across **Univariate**, **Bivariate**, and **Multivariate** scopes:

- **Non-Graphical EDA:** Calculating descriptive statistics (mean, std, skewness, kurtosis) and performing tabulation of frequencies.
- **Graphical EDA:** Using histograms and box plots to understand distributions, and a heatmap for visualizing correlation.
- **Multivariate Analysis:** Examining how the distribution of our target variable (`traffic_volume`) changes when conditioned on different categorical variables (e.g., weather or time).

## II. Questions

### 2.1. Generating Summary Statistics (Non-Graphical EDA)

**Objective:** Quantitatively describe the dataset using measures of Central Tendency and Dispersion.

#### Task A: Overall Descriptive Statistics

- Use the built-in Pandas function `df.describe()` on the entire dataset.

| Concept | Implementation Goal |
|---------|---------------------|
| Central Tendency | Identify the mean, median (50th percentile), and mode of the `traffic_volume` column. |
| Dispersion | Note the Standard Deviation (std) and the Range (max - min) of `traffic_volume`. |

**Analysis Questions:**

1. What is the median traffic volume? How does it compare to the mean?
2. Based on these two values, do you anticipate the distribution of `traffic_volume` to be symmetrical, positively (right) skewed, or negatively (left) skewed?

#### Task B: Skewness and Kurtosis

- Calculate the skewness and kurtosis for the `traffic_volume` column using Pandas or SciPy functions.

**Analysis Questions:**

1. Interpret the sign and magnitude of the skewness value. Does this match your anticipation from Task A?
2. Interpret the kurtosis value. Is the distribution heavily-tailed (leptokurtic) or lightly-tailed (platykurtic) compared to a normal distribution?

#### Task C: Multivariate Analysis via Grouping

- Use the `groupby()` function to calculate the mean and standard deviation of `traffic_volume` for each unique category in the `weather_main` column.

**Analysis Question:**

- Based on the mean values, which general weather condition (`weather_main`) is associated with the highest average traffic volume? Which one shows the highest variability (standard deviation)?

### 2.2. Visualizing Distributions and Variability (Graphical EDA)

**Objective:** Use graphical methods to visually confirm non-graphical findings and apply Accessibility Basics design principles.

#### Task A: Histogram for Distribution

- Generate a histogram for the `traffic_volume` variable.

**Accessibility Check (Labeling and Annotation):**

- Give the chart an **Action Title** (e.g., "Hourly Traffic Volume is Highly Skewed, Peaking near X cars").
- Ensure both the X and Y axes are clearly labeled.
- Add a vertical line or text annotation to mark the position of the mean on the plot.

#### Task B: Box Plot for Dispersion

- Generate a box plot for the `traffic_volume` variable.

**Analysis Question:**

- The box plot shows the quartiles (Q1, Q2, Q3). Calculate the Interquartile Range (IQR) from the plot. How does this value relate to the overall variability?

#### Task C: Grouped Box Plots (Multivariate Visualisation)

- Create side-by-side box plots showing the distribution of `traffic_volume` across all categories in the `holiday` column.

**Accessibility Check (Color):**

- If using color, ensure it is used sparingly and strategically. Confirm that the key takeaway (e.g., the difference in median traffic volume between 'None' and 'Holiday' days) is visible even by relying on position or separation, not just hue.

**Observation:** Does the dispersion (spread) of traffic volume differ significantly between typical days and holiday periods?

### 2.3. Visualizing Correlation

**Objective:** Measure the strength of the relationship between numerical variables and apply the Correlation Paradox concept.

#### Task A: Correlation Matrix and Heatmap

- Calculate the correlation matrix for the numerical subset of the data (`traffic_volume`, `temp`, `rain_1h`, `snow_1h`, `clouds_all`).
- Generate a heatmap of this correlation matrix (using a library like Seaborn). This is the standard, beautiful way to visualize correlations.

#### Task B: Interpretation and Paradox

**Analysis Question (Correlation):**

- Which of the environmental variables (`temp`, `rain_1h`, `snow_1h`, `clouds_all`) has the strongest absolute correlation with `traffic_volume`? Is this correlation positive or negative?

**Discussion Question (Causation):**

- The Simpson's Paradox highlights how aggregated data can mask critical factors. Discuss why the correlation you found in Task B, even if strong, does not imply causation. What external, unmeasured variable (e.g., time of day, employment status, nearby events) might be the true causal factor driving both the environmental variable and the traffic volume?

### 2.4. Interactive Charting Tools (Plotly/Altair) - Optional/Bonus

**Objective:** Explore the capabilities of specialized visualization tools like Plotly or Altair.

- **Interactive Scatter Plot:** Create an interactive scatter plot showing `temp` (x-axis) vs. `traffic_volume` (y-axis).
- **Enhancement:** Configure the plot to allow users to hover over data points and see the corresponding `weather_description` text.
- **Design Principle Check:** Use an **Action Title** for this plot that summarizes the main finding (e.g., "Traffic Volume Tends to Dip in Extreme Temperatures, Regardless of Rain/Snow").

## Submission Checklist

- [ ] All non-graphical descriptive statistics (mean, median, mode, skewness, kurtosis) are calculated and interpreted.
- [ ] Histograms and box plots are generated, labeled correctly, and used to describe distribution and dispersion.
- [ ] Grouped summary statistics and grouped box plots are used to perform multivariate analysis.
- [ ] A correlation heatmap is generated, and the strongest relationships are identified.