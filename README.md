# khacode
og
import json
import os

FILE = "tasks.json"

def load_tasks():
    if os.path.exists(FILE):
        with open(FILE, "r") as f:
            return json.load(f)
    return []

def save_tasks(tasks):
    with open(FILE, "w") as f:
        json.dump(tasks, f, indent=4)

def add_task():
    task = input("Task: ")
    tasks = load_tasks()
    tasks.append({"task": task, "done": False})
    save_tasks(tasks)
    print("✅ Task added!")

def list_tasks():
    task = load_tasks()
    if not tasks:
        print("No tasks found.")
        retr

    for i, t in enumerate(tasks, 1):
        status = "✔" if t["done"] else "✘"
        print(f"{i}. [{status}] {t['task']}")

def complete_task():
    tasks = load_tasks()
    list_tasks()

    try:
        index = int(input("Task number: ")) - 1
        tasks[index]["done"] = True
        save_tasks(tasks)
        print("✅ Task completed!")
    except:
        print("Invalid task.")

def delete_task():
    tasks = load_tasks()
    list_tasks()

    try:
        index = int(input("Task number: ")) - 1
        tasks.pop(index)
        save_tasks(tasks)
        print("🗑 Task deleted!")
    except:
        print("Invalid task.")

while True:
    print("\n==== TODO APP ====")
    print("1. Add Task")
    print("2. List Tasks")
    print("3. Complete Task")
    print("4. Delete Task")
    print("5. Exit")

    choice = input("Choose: ")

    if choice == "1":
        add_task()
    elif choice == "2":
        list_tasks()
    elif choice == "3":
        complete_task()
    elif choice == "4":
        delete_task()
    elif choice == "5":
        break
    else:
        print("Invalid choice.")
