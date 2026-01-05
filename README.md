# Student-management-system-
Student Management System project developed for academic submission.
code:
import tkinter as tk
from tkinter import messagebox

students = []

def add_student():
    data = (e1.get(), e2.get(), e3.get())
    if "" in data:
        messagebox.showerror("Error", "All fields required")
    else:
        students.append(data)
        messagebox.showinfo("Success", "Student Added")
        clear()

def view_students():
    lb.delete(0, tk.END)
    for s in students:
        lb.insert(tk.END, s)

def delete_student():
    try:
        students.pop(lb.curselection()[0])
        view_students()
    except:
        messagebox.showerror("Error", "Select a student")

def clear():
    e1.delete(0, tk.END)
    e2.delete(0, tk.END)
    e3.delete(0, tk.END)

root = tk.Tk()
root.title("Student Management System")
root.geometry("400x350")

for text in ["Name", "Roll No", "Course"]:
    tk.Label(root, text=text).pack()

e1, e2, e3 = tk.Entry(root), tk.Entry(root), tk.Entry(root)
e1.pack(); e2.pack(); e3.pack()

tk.Button(root, text="Add", command=add_student).pack()
tk.Button(root, text="View", command=view_students).pack()
tk.Button(root, text="Delete", command=delete_student).pack()

lb = tk.Listbox(root, width=45)
lb.pack(pady=10)

root.mainloop()