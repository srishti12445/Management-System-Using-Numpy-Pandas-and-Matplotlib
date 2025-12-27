# Management-System-Using-Numpy-Pandas-and-Matplotlib
The management project is designed to analyze organizational management practices and suggest improvements for better efficiency and performance. It focuses on planning, leadership, decision-making, and resource utilization to help organizations achieve their objectives.
# Attendance Management System using NumPy, Pandas & Matplotlib

## 📌 Project Overview
The Attendance Management System is a Python-based project designed to manage, analyze, and visualize student attendance data efficiently. This system uses NumPy for numerical operations, Pandas for data handling, and Matplotlib for graphical representation. It is suitable for college-level academic projects.

---

## 🎯 Objectives
- Store attendance records using NumPy arrays
- Manage and analyze data using Pandas DataFrames
- Calculate attendance percentage automatically
- Identify students with low attendance
- Visualize attendance data using bar charts

---

## 🛠️ Technologies Used
- **Python 3**
- **NumPy**
- **Pandas**
- **Matplotlib**

---

## 📂 Project Structure

---

## ⚙️ How to Run the Project
1. Install required libraries:

2. Run the Python file:

3. The program will:
- Display attendance records
- Calculate attendance percentage
- Show attendance graph
- Generate a CSV report

---

## 📊 Features
- Automatic attendance calculation
- Low attendance detection (<75%)
- Graphical visualization
- CSV report generation
- Easy to modify for Library or Restaurant Management Systems

---

## 📈 Output
- Attendance report in tabular format
- Bar chart showing attendance percentage
- CSV file for future reference

---

## ✅ Advantages
- Simple and easy to understand
- Reduces manual calculation errors
- Efficient data management
- Suitable for real-world scenarios

---

## 🔮 Future Enhancements
- Add database integration
- GUI-based interface
- Web-based attendance system
- Login authentication

---

## 👨‍🎓 Author
**Srishti kumari**  
BTECH Student  

---

## 📜 License
This project is created for educational purposes only.
1️⃣ Import Required Libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
2️⃣ Create Student Data (using NumPy)
# Student basic data
student_ids = np.array([101, 102, 103, 104, 105])
names = np.array(["Aman", "Riya", "Rahul", "Sneha", "Karan"])
classes = np.array(["BTECH", "BTECH", "BTECH", "BTECH", "BTECH"])
3️⃣ Attendance Data (Present = 1, Absent = 0)
attendance = np.array([
    [1, 1, 0, 1, 1],  # Aman
    [1, 1, 1, 1, 1],  # Riya
    [0, 1, 1, 0, 1],  # Rahul
    [1, 0, 1, 1, 1],  # Sneha
    [1, 1, 1, 1, 0]   # Karan
])
4️⃣ Create Pandas DataFrame
attendance_df = pd.DataFrame(
    attendance,
    columns=["Day1", "Day2", "Day3", "Day4", "Day5"]
)

attendance_df.insert(0, "Student Name", names)
attendance_df.insert(0, "Student ID", student_ids)

print(attendance_df)
5️⃣ Calculate Attendance Percentage
attendance_df["Total Present"] = attendance_df.iloc[:, 2:7].sum(axis=1)
attendance_df["Attendance %"] = (attendance_df["Total Present"] / 5) * 100

print("\nFinal Attendance Report:\n")
print(attendance_df)
6️⃣ Find Low Attendance Students
low_attendance = attendance_df[attendance_df["Attendance %"] < 75]

print("\nStudents with Low Attendance (<75%):\n")
print(low_attendance)
7️⃣ Visualization using Matplotlib
plt.figure()
plt.bar(attendance_df["Student Name"], attendance_df["Attendance %"])
plt.xlabel("Student Name")
plt.ylabel("Attendance Percentage")
plt.title("Student Attendance Report")
plt.show()
8️⃣ Save Report to CSV
attendance_df.to_csv("attendance_report.csv", index=False)
print("Attendance report saved successfully.")


