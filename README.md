class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})
        print(f"Task '{task}' added.")

    def remove_task(self, task):
        for t in self.tasks:
            if t["task"] == task:
                self.tasks.remove(t)
                print(f"Task '{task}' removed.")
                return
        print(f"Task '{task}' not found.")

    def mark_task_completed(self, task):
        for t in self.tasks:
            if t["task"] == task:
                t["completed"] = True
                print(f"Task '{task}' marked as completed.")
                return
        print(f"Task '{task}' not found.")

    def show_tasks(self):
        if not self.tasks:
            print("No tasks found.")
        else:
            print("Tasks:")
            for i, t in enumerate(self.tasks, start=1):
                status = "Completed" if t["completed"] else "Not Completed"
                print(f"{i}. {t['task']} - {status}")


def main():
    task_manager = TaskManager()

    while True:
        print("\nTask Manager Menu:")
        print("1. Add Task")
        print("2. Remove Task")
        print("3. Mark Task as Completed")
        print("4. Show Tasks")
        print("5. Quit")

        choice = input("Enter your choice (1/2/3/4/5): ")

        if choice == "1":
            task = input("Enter the task: ")
            task_manager.add_task(task)
        elif choice == "2":
            task = input("Enter the task to remove: ")
            task_manager.remove_task(task)
        elif choice == "3":
            task = input("Enter the task to mark as completed: ")
            task_manager.mark_task_completed(task)
        elif choice == "4":
            task_manager.show_tasks()
        elif choice == "5":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()

