# 📊 Practical Work: COVID-19 Visualisation Critique and Redesign

This lab addresses all content from Week 1 by requiring students to critique a real-world, potentially misleading COVID-19 chart, identify its flaws using Tufte's principles and storytelling concepts, and then create an effective, explanatory visualisation using the same underlying data.

## 📝 Part 1: The Misleading Chart Case Study

### Case Study: The Georgia DPH Chart Analysis

We will analyze the specific misleading chart published by the Georgia Department of Public Health (DPH) in May 2020, using the detailed critique provided by Columbia Law School's Climate Center.

**Reference Article**: [COVID-19 Data Misrepresented by Georgia Health Department](https://climate.law.columbia.edu/content/covid-19-data-misrepresented-georgia-health-department)

### The Georgia DPH Chart Incident

The Georgia Department of Public Health published a chart in May 2020 that plotted new confirmed COVID-19 cases over a 14-day period but intentionally reordered the dates on the x-axis to create a false impression of a consistent decline in cases. Instead of chronological order, the dates were arranged from highest case count to lowest.

### Discussion Points (Concepts & Principles)

- **Clarity & Perception**: The x-axis ordering was manipulated by sorting dates based on case counts (descending order) rather than chronological sequence. This created the visual illusion of a steady downward trend when no such trend existed in the actual temporal data.

- **Context (Purpose)**: The implied message suggested COVID-19 cases were consistently declining, potentially to support premature reopening policies. This contradicted the actual public health reality where cases were fluctuating without a clear downward trend.

- **Edward Tufte's Principles**: Multiple principles were violated:
  - **Integrity Principle**: The chart fundamentally distorted what the data actually showed
  - **Clarity Principle**: The non-chronological ordering confused rather than clarified the data
  - **Comparative Principle**: Made meaningful comparisons over time impossible

## 🛠️ Part 2: Python Lab - Exploratory vs. Explanatory Visualisation

You will use USAFacts COVID-19 data for Georgia to recreate the analysis and build an effective, honest chart.

### Data Set Resource

**USAFacts COVID-19 Data for Georgia**

- **Resource**: USAFacts provides reliable, publicly-available COVID-19 data with state and county-level granularity
- **Website**: [USAFacts Coronavirus Spread Map - Georgia](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/state/georgia/)
- **Data Access**: Download the CSV data for Georgia cases from the USAFacts website
- **Focus**: We'll use daily new cases data for Georgia during the relevant period (May 2020)

### Lab Steps

#### 1. Data Loading and Preparation (Python/Pandas)

- Download and load the Georgia COVID-19 cases CSV file from USAFacts into a Pandas DataFrame
- Filter the data for the specific time period surrounding the original misleading chart (May 2020)
- Extract relevant columns: `date`, `confirmed_cases` (or similar), and calculate daily new cases if needed
- Compute a 7-day rolling average for new cases to smooth out day-of-week reporting effects

#### 2. Exploratory Analysis (Matplotlib/Seaborn)

- Create a simple line plot of date vs. daily new cases (unsmoothed) for Georgia during May 2020
- This exploratory view will show the raw, noisy data that was originally manipulated

#### 3. The Misleading Recreation (Educational Purpose)

- **Recreation Exercise**: Reproduce the misleading effect by:
  - Selecting a two-week segment from the Georgia data
  - Sorting the dates by case count in descending order (as the original chart did)
  - Plotting this manipulated data as a bar or line chart
- **Critical Analysis**: Write a brief critique comparing your recreated misleading chart with the original Georgia DPH chart

#### 4. Explanatory Visualisation (Seaborn/Matplotlib)

- Create an honest, explanatory line plot showing:
  - The 7-day rolling average of new cases in Georgia during the relevant period
  - Proper chronological x-axis ordering
- **Storytelling Elements**:
  - **Annotations**: Mark key dates and events (e.g., "Original Misleading Chart Published")
  - **Comparative Elements**: Show both the raw data and smoothed trend for context
  - **Clear Title**: "COVID-19 Cases in Georgia (May 2020) - Proper Chronological View"
  - **Axis Labels**: Clear, unambiguous date and case count labels

## 📦 Deliverables

Your final practical work should include:

### Part 1 Critique
- A detailed analysis of the Georgia DPH misleading chart based on the Columbia Law School article
- Identification of specific visual manipulations and violations of data visualization principles
- Connection to course concepts: Perception, Tufte's principles, and Context

### Part 2 Code and Visualisations
- A clean, commented Python script that loads and processes the USAFacts Georgia COVID-19 data
- The Exploratory Plot showing raw daily cases for Georgia
- The recreated Misleading Chart (for educational comparison)
- The final Explanatory Plot with proper chronological ordering and annotations
- Brief commentary on the differences between the misleading and proper visualizations
