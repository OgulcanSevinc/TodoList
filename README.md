Todo List
This project is a simple task management application developed in Vue.js. It allows users to add, display, and hide completed tasks in a list.

Features
Add a Task: Users can add new tasks by entering text in the input field and clicking the "Add" button.
Complete a Task: Users can mark tasks as "completed" by checking the checkbox next to the task.
Hide Completed Tasks: An option allows users to hide tasks that have been marked as completed.
Task Sorting: Tasks are automatically sorted, with incomplete tasks displayed first.
Project Structure
Template
The template contains:

A text field to add new tasks.
A task list with checkboxes to mark tasks as completed.
A checkbox to toggle hiding/showing completed tasks.
Behavior
Tasks are managed through a reactive todos array.
New tasks are added to this array with a completed property initialized to false.
Tasks are sorted based on their completion status (incomplete tasks are shown first).
When the Hide Completed Tasks option is enabled, only incomplete tasks are displayed.
Styles
Completed tasks appear grayed out and strikethrough due to the .completed CSS class.

