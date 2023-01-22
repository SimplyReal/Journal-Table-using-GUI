# Journal-Table-using-GUI
import tkinter as tk
from tkinter import ttk
def add_entry():
    date_text = date_entry.get()
    entry_text = entry_entry.get("1.0",'end-1c')

    # add the entry to the table
    table.insert("", "end", values=(date_text, entry_text))

    # clear the entry fields
    date_entry.delete(0, "end")
    entry_entry.delete("1.0", "end")

# create the main window
root = tk.Tk()
root.title("Journal Entry")

# create the label and entry widgets for the date
date_label = tk.Label(root, text="Date:")
date_label.grid(row=0, column=0)
date_entry = tk.Entry(root)
date_entry.grid(row=0, column=1)

# create the label and entry widgets for the entry
entry_label = tk.Label(root, text="Entry:")
entry_label.grid(row=1, column=0)
entry_entry = tk.Text(root, height=5, width=30)
entry_entry.grid(row=1, column=1)

# create the table to display the journal entries
table = ttk.Treeview(root, columns=("date", "entry"), show="headings")
table.heading("date", text="Date")
table.heading("entry", text="Entry")
table.grid(row=2, column=0, columnspan=2)

# create the add entry button
add_button = tk.Button(root, text="Add Entry", command=add_entry)
add_button.grid(row=3, column=0, columnspan=2)

root.mainloop()
