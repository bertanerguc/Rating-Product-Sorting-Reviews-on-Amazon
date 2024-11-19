# 🌟 Rating Product & Sorting Reviews on Amazon

This project tackles two critical problems in e-commerce:
1. **Accurate Product Rating**: Ensuring that product ratings are calculated effectively based on historical reviews.
2. **Sorting Reviews**: Identifying the most helpful reviews to display prominently, enhancing customer trust and satisfaction.

---

## 🚀 Project Overview

### 📝 Problem Statement
In e-commerce, misleading ratings and poorly sorted reviews can lead to revenue loss and customer dissatisfaction. By solving these issues:
- Sellers can boost product visibility and sales.
- Customers can make informed purchasing decisions.
- E-commerce platforms can enhance user satisfaction and loyalty.

This project focuses on:
1. Calculating a **time-based weighted average rating** for products.
2. Identifying the top **20 most helpful reviews** using statistical scoring techniques.

---

## 📂 Dataset Description

The dataset includes reviews for a popular product in the **Electronics** category.

| Feature         | Description                                                       |
|-----------------|-------------------------------------------------------------------|
| `reviewerID`    | Unique identifier for the reviewer                                |
| `asin`          | Unique identifier for the product                                 |
| `reviewerName`  | Name of the reviewer                                              |
| `helpful`       | Helpful votes in the format (helpful_yes/total_votes)             |
| `reviewText`    | Full text of the review                                           |
| `overall`       | Rating given by the reviewer                                      |
| `summary`       | Summary of the review                                             |
| `unixReviewTime`| Review time in Unix format                                        |
| `reviewTime`    | Review time in raw format                                         |
| `day_diff`      | Number of days since the review was posted                        |
| `helpful_yes`   | Number of helpful votes                                           |
| `total_vote`    | Total number of votes                                             |

---

## 🔧 Key Features

### 🛠 Tasks

1. **Calculate Weighted Average Rating**:
   - Compute a time-based weighted average to give more importance to recent reviews.
   - Compare the weighted average with the overall average rating.
2. **Sort Reviews**:
   - Generate new scoring metrics:
     - **Positive-Negative Difference**: Helpful votes minus non-helpful votes.
     - **Average Rating**: Ratio of helpful votes to total votes.
     - **Wilson Lower Bound (WLB)**: A statistical method for ranking helpful reviews.
   - Rank reviews using the **Wilson Lower Bound** score.

---

## 📈 Project Workflow

### 1️⃣ Calculate Weighted Average Rating
- Use review timestamps to assign weights to reviews based on recency:
  - Reviews in the most recent quarter: **50% weight**.
  - Reviews in the second most recent quarter: **25% weight**.
  - Reviews in the third most recent quarter: **15% weight**.
  - Older reviews: **10% weight**.
- Compute and compare the weighted and unweighted average ratings.

### 2️⃣ Generate Review Scores
- Create a new column `helpful_no`:
  - `helpful_no = total_vote - helpful_yes`
- Calculate scoring metrics for each review:
  - **Positive-Negative Difference (score_pos_neg_diff)**:
    - Formula: `helpful_yes - helpful_no`
  - **Average Rating (score_average_rating)**:
    - Formula: `helpful_yes / total_vote`
  - **Wilson Lower Bound (WLB)**:
    - Formula: Statistical calculation using the binomial distribution to rank helpful reviews.

### 3️⃣ Identify Top Reviews
- Rank reviews by their **Wilson Lower Bound** score.
- Select the top 20 reviews to display prominently.

---

## 📊 Results

### 🎯 Example Outputs

#### Weighted Average Rating:
- **Overall Average Rating**: 4.58  
- **Time-Based Weighted Average Rating**: 4.68  

#### Top 20 Reviews (by WLB Score):
- Reviews are ranked to ensure the most reliable and helpful feedback is highlighted for potential customers.

---

## 🛠 Tools and Libraries

- **Python**  
- **Pandas**  
- **NumPy**  
- **Scipy**  
- **Matplotlib**  

---

## 🌟 Contribution

Contributions are welcome!  
Feel free to fork this repository, create issues, or submit pull requests for improvements.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
