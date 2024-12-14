Step-by-Step Guide
1. Importing Required Libraries
First, you need to import the necessary libraries. For a basic GUI calculator in Python, we’ll use tkinter.

python
import tkinter as tk
2. Setting Up the Main Window
Create the main window for the calculator application.

python
root = tk.Tk()
root.geometry("400x600")
root.title("Simple Calculator")
3. Creating the Display
This will be the area where the input and result are shown.

python
input_field = tk.Entry(root, font="lucida 20 bold")
input_field.pack(fill=tk.BOTH, ipadx=8, pady=10)
4. Button Click Function
Define a function to handle button clicks, updating the display accordingly.

python
def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = str(eval(input_field.get()))
            input_field.delete(0, tk.END)
            input_field.insert(tk.END, result)
        except Exception as e:
            input_field.delete(0, tk.END)
            input_field.insert(tk.END, "Error")
    elif text == "C":
        input_field.delete(0, tk.END)
    else:
        input_field.insert(tk.END, text)
5. Creating Buttons
Set up the buttons for the digits and operations, and arrange them in a grid layout.

python
button_frame = tk.Frame(root)
button_frame.pack()

buttons = [
    "7", "8", "9", "+",
    "4", "5", "6", "-",
    "1", "2", "3", "*",
    "C", "0", "=", "/"
]

row_val = 0
col_val = 0
for button_text in buttons:
    button = tk.Button(button_frame, text=button_text, font="lucida 15 bold")
    button.grid(row=row_val, column=col_val, padx=10, pady=10)
    button.bind("<Button-1>", click)
    col_val += 1
    if col_val > 3:
        col_val = 0
        row_val += 1
6. Running the Application
Finally, start the main loop of the application.

python
root.mainloop()
Full Code
Here’s the complete code for the calculator:

python
import tkinter as tk

def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = str(eval(input_field.get()))
            input_field.delete(0, tk.END)
            input_field.insert(tk.END, result)
        except Exception as e:
            input_field.delete(0, tk.END)
            input_field.insert(tk.END, "Error")
    elif text == "C":
        input_field.delete(0, tk.END)
    else:
        input_field.insert(tk.END, text)

root = tk.Tk()
root.geometry("400x600")
root.title("Simple Calculator")

input_field = tk.Entry(root, font="lucida 20 bold")
input_field.pack(fill=tk.BOTH, ipadx=8, pady=10)

button_frame = tk.Frame(root)
button_frame.pack()

buttons = [
    "7", "8", "9", "+",
    "4", "5", "6", "-",
    "1", "2", "3", "*",
    "C", "0", "=", "/"
]

row_val = 0
col_val = 0
for button_text in buttons:
    button = tk.Button(button_frame, text=button_text, font="lucida 15 bold")
    button.grid(row=row_val, column=col_val, padx=10, pady=10)
    button.bind("<Button-1>", click)
    col_val += 1
    if col_val > 3:
        col_val = 0
        row_val += 1

root.mainloop()
This code sets up a basic calculator with buttons for numbers and basic operations. Each button click updates the display, and the = button evaluates the expression entered.
