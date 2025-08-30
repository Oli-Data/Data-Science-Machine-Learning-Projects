# 📊 Chicago Public Schools Analysis (2011–2012)

This project explores factors influencing academic performance in **Chicago Public Schools** during the 2011–2012 school year.  
The dataset includes attendance rates, school environment scores, and student achievement levels across elementary and middle schools.  

---

## 🚀 Project Overview
- **Data Source:** [Chicago Public Schools – Progress Report Cards 2011–2012](https://data.cityofchicago.org/Education/Chicago-Public-Schools-Progress-Report-Cards-2011-/9xs2-f89t)  
- **Tools Used:** R, dplyr, ggplot2  
- **Focus:**  
  - Cleaning and transforming student performance data  
  - Filtering out incomplete/missing values (NDA fields, high schools omitted)  
  - Visualizing attendance and environment scores vs. grade-level performance  
  - Calculating correlations using Pearson’s formula  

---

## 📈 Key Insights
- **Environment Scores** showed only weak correlations with student achievement.  
- **Student Attendance** had a much stronger relationship with academic success, especially in **grades 3–8**.  
- Preschool–2nd grade showed little correlation compared to older students.  

---

## 📌 Files
- `Chicago_Public_Schools_-_Progress_Report_Cards__2011-2012_.csv` → original dataset  
- `analysis.Rmd` → R Markdown with full analysis, code, and visualizations  
- `analysis.pdf` → rendered report  

---

## 🔮 Next Steps
- Extend analysis with more recent CPS data  
- Explore additional variables (teacher quality, funding, demographics)  
- Incorporate regression models for prediction  
