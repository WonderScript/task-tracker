# Task Tracker
A task tracker implemented by go lang. [Link to project](https://roadmap.sh/projects/task-tracker).

## UML Design for Task Tracker CLI Application

### Use Case Diagram
#### Actors:
- **User**: Interacts with the CLI to manage tasks.

#### Use Cases:
1. **Add Task**: Add a new task with a title and description.
2. **Update Task**: Modify an existing task.
3. **Delete Task**: Remove a task.
4. **Mark Task**: Change the status of a task to "In Progress" or "Done."
5. **List All Tasks**: View all tasks.
6. **List Done Tasks**: View tasks marked as "Done."
7. **List Not Done Tasks**: View tasks that are not marked as "Done."
8. **List In Progress Tasks**: View tasks marked as "In Progress."

### Class Diagram

#### Classes:

1. **Task**
   - Attributes:
     - `id: string`
     - `title: string`
     - `description: string`
     - `status: string` (e.g., "Not Done", "In Progress", "Done")
   - Methods:
     - `updateTitle(newTitle: string): void`
     - `updateDescription(newDescription: string): void`
     - `changeStatus(newStatus: string): void`

2. **TaskManager**
   - Attributes:
     - `tasks: Task[]`
     - `filePath: string`
   - Methods:
     - `addTask(title: string, description: string): void`
     - `updateTask(id: string, title?: string, description?: string): void`
     - `deleteTask(id: string): void`
     - `markTask(id: string, status: string): void`
     - `listAllTasks(): Task[]`
     - `listTasksByStatus(status: string): Task[]`
     - `loadTasks(): void`
     - `saveTasks(): void`

3. **CLI**
   - Attributes:
     - `taskManager: TaskManager`
   - Methods:
     - `parseInput(input: string[]): void`
     - `handleCommand(command: string, args: string[]): void`

### JSON Storage Structure
```json
[
  {
    "id": "1",
    "title": "Learn UML",
    "description": "Understand how to create UML diagrams",
    "status": "In Progress"
  },
  {
    "id": "2",
    "title": "Build CLI",
    "description": "Create a command line interface for task tracking",
    "status": "Not Done"
  }
]
```

### Sequence Diagram for "Add Task"
1. **User**: Inputs command `add "Learn UML" "Understand UML basics"`.
2. **CLI**: Parses the input and calls `taskManager.addTask("Learn UML", "Understand UML basics")`.
3. **TaskManager**: Creates a new `Task` object and adds it to the `tasks` list.
4. **TaskManager**: Saves the updated tasks to the JSON file.
5. **CLI**: Displays a success message.

### Activity Diagram for "List Tasks"
1. User selects the "List All Tasks" command.
2. CLI calls `taskManager.listAllTasks()`.
3. TaskManager reads the tasks from memory or loads them from the JSON file if not already loaded.
4. TaskManager returns the list of tasks to the CLI.
5. CLI formats and displays the tasks to the user.

This UML design provides a structured overview of the system's functionality and components, making implementation straightforward and modular.



## UML Diagram
![image](./Untitled%20diagram-2025-01-25-153412.png)
