# Coding-Raja-Technologies-Internship
import os
import json

class Todo:
    def __init__(self):
        self.tasks = []
        self.load_tasks()

    def load_tasks(self):
        if os.path.exists('tasks.json'):
            with open('tasks.json', 'r') as f:
                self.tasks = json.load(f)

    def save_tasks(self):
        with open('tasks.json', 'w') as f:
            json.dump(self.tasks, f)

    def add_task(self, description, priority='low', due_date=None):
        task = {
            'description': description,
            'priority': priority,
            'due_date': due_date,
            'completed': False
        }
        self.tasks.append(task)
        self.save_tasks()

    def remove_task(self, task_id):
        task = self.get_task(task_id)
        if task:
            self.tasks.remove(task)
            self.save_tasks()

    def get_task(self, task_id):
        for task in self.tasks:
            if task['description'] == task_id:
                return task
        return None

    def complete_task(self, task_id):
        task = self.get_task(task_id)
        if task:
            task['completed'] = True
            self.save_tasks()

    def view_tasks(self):
        for task in self.tasks:
            print(f"{task['description']} - {task['priority']} - {task['due_date']} - {task['completed']}")

if __name__ == "__main__":
    todo = Todo()
    while True:
        print("\nTo-Do List Application")
        print("1. Add Task")
        print("2. Remove Task")
        print("3. Complete Task")
        print("4. View Tasks")
        print("5. Exit")

        choice
