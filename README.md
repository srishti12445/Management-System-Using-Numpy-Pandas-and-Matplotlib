import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

student_ids = np.array([101, 102, 103, 104, 105])
names = np.array(["Aman", "Riya", "Rahul", "Sneha", "Karan"])
classes = np.array(["BTECH", "BTECH", "BTECH", "BTECH", "BTECH"])

attendance = np.array([
    [1, 1, 0, 1, 1],  # Aman
    [1, 1, 1, 1, 1],  # Riya
    [0, 1, 1, 0, 1],  # Rahul
    [1, 0, 1, 1, 1],  # Sneha
    [1, 1, 1, 1, 0]   # Karan
])

attendance_df = pd.DataFrame(
    attendance,
    columns=["Day1", "Day2", "Day3", "Day4", "Day5"]
)

attendance_df.insert(0, "Student Name", names)
attendance_df.insert(0, "Student ID", student_ids)

print(attendance_df)

attendance_df["Total Present"] = attendance_df.iloc[:, 2:7].sum(axis=1)
attendance_df["Attendance %"] = (attendance_df["Total Present"] / 5) * 100

print("\nFinal Attendance Report:\n")
print(attendance_df)

low_attendance = attendance_df[attendance_df["Attendance %"] < 75]

print("\nStudents with Low Attendance (<75%):\n")
print(low_attendance)

plt.figure()
plt.bar(attendance_df["Student Name"], attendance_df["Attendance %"])
plt.xlabel("Student Name")
plt.ylabel("Attendance Percentage")
plt.title("Student Attendance Report")
plt.show()

attendance_df.to_csv("attendance_report.csv", index=False)
print("Attendance report saved successfully.")


