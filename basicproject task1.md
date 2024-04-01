# sampleproject
Develop a Python task management app for adding, removing, listing, prioritizing, and receiving task recommendations based on task descriptions.
class Task:
    def __init__(self, description, priority=0):
        self.description = description
        self.priority = priority

    def __str__(self):
        return f"{self.description} (Priority: {self.priority})"


class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, description, priority=0):
        task = Task(description, priority)
        self.tasks.append(task)

    def remove_task(self, index):
        del self.tasks[index]

    def list_tasks(self):
        if not self.tasks:
            print("No tasks.")
        else:
            for i, task in enumerate(self.tasks):
                print(f"{i + 1}. {task}")

    def prioritize_task(self, index, priority):
        self.tasks[index].priority = priority

    def recommend_task(self, keyword):
        recommended_tasks = []
        for task in self.tasks:
            if keyword.lower() in task.description.lower():
                recommended_tasks.append(task)
        if not recommended_tasks:
            print("No tasks matching the keyword.")
        else:
            print("Recommended tasks:")
            for task in recommended_tasks:
                print(task)


def main():
    task_manager = TaskManager()

    while True:
        print("\nTask Management Menu:")
        print("1. Add Task")
        print("2. Remove Task")
        print("3. List Tasks")
        print("4. Prioritize Task")
        print("5. Recommend Task")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            description = input("Enter task description: ")
            priority = int(input("Enter task priority (default is 0): "))
            task_manager.add_task(description, priority)
        elif choice == "2":
            task_manager.list_tasks()
            index = int(input("Enter task number to remove: ")) - 1
            task_manager.remove_task(index)
        elif choice == "3":
            task_manager.list_tasks()
        elif choice == "4":
            task_manager.list_tasks()
            index = int(input("Enter task number to prioritize: ")) - 1
            priority = int(input("Enter new priority: "))
            task_manager.prioritize_task(index, priority)
        elif choice == "5":
            keyword = input("Enter keyword for task recommendation: ")
            task_manager.recommend_task(keyword)
        elif choice == "6":
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
