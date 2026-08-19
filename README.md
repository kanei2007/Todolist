# Ex03 To-Do List using JavaScript
## Date:19.08.2026

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>TaskSphere - Todo Application</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <div class="app">

        <!-- HEADER -->
        <header class="header">

            <div>
                <h1>Task<span>Sphere</span> ✨</h1>

                <p>
                    Organize your tasks. Manage your time. Stay productive.
                </p>
            </div>

            <button id="themeBtn" class="theme-btn">
                🌙
            </button>

        </header>


        <!-- STATISTICS -->

        <section class="stats">

            <div class="stat-card">

                <div class="stat-icon">
                    📋
                </div>

                <div>
                    <h3 id="totalTasks">0</h3>
                    <p>Total Tasks</p>
                </div>

            </div>


            <div class="stat-card">

                <div class="stat-icon">
                    ⏳
                </div>

                <div>
                    <h3 id="pendingTasks">0</h3>
                    <p>Pending Tasks</p>
                </div>

            </div>


            <div class="stat-card">

                <div class="stat-icon">
                    ✅
                </div>

                <div>
                    <h3 id="completedTasks">0</h3>
                    <p>Completed</p>
                </div>

            </div>


            <div class="stat-card">

                <div class="stat-icon">
                    📈
                </div>

                <div>
                    <h3 id="progress">0%</h3>
                    <p>Progress</p>
                </div>

            </div>

        </section>


        <!-- ADD TASK -->

        <section class="task-form">

            <input
                type="text"
                id="taskInput"
                placeholder="What needs to be done?"
            >


            <select id="category">

                <option value="General">
                    📌 General
                </option>

                <option value="Study">
                    📚 Study
                </option>

                <option value="Work">
                    💼 Work
                </option>

                <option value="Personal">
                    🏠 Personal
                </option>

                <option value="Shopping">
                    🛒 Shopping
                </option>

            </select>


            <select id="priority">

                <option value="Low">
                    🟢 Low
                </option>

                <option value="Medium">
                    🟡 Medium
                </option>

                <option value="High">
                    🔴 High
                </option>

            </select>


            <input
                type="date"
                id="dueDate"
            >


            <button
                onclick="addTask()"
                class="add-btn"
            >
                + Add Task
            </button>

        </section>


        <!-- SEARCH AND FILTER -->

        <section class="search-box">

            <input
                type="text"
                id="searchInput"
                placeholder="🔍 Search your tasks..."
                oninput="displayTasks()"
            >


            <select
                id="filter"
                onchange="displayTasks()"
            >

                <option value="all">
                    All Tasks
                </option>

                <option value="pending">
                    Pending
                </option>

                <option value="completed">
                    Completed
                </option>

                <option value="high">
                    High Priority
                </option>

            </select>


            <select
                id="sort"
                onchange="displayTasks()"
            >

                <option value="newest">
                    Newest
                </option>

                <option value="oldest">
                    Oldest
                </option>

                <option value="priority">
                    Priority
                </option>

            </select>

        </section>


        <!-- PROGRESS -->

        <section class="progress-container">

            <div class="progress-info">

                <span>
                    🎯 Overall Progress
                </span>

                <span id="progressText">
                    0%
                </span>

            </div>


            <div class="progress-bar">

                <div id="progressBar"></div>

            </div>

        </section>


        <!-- TASK LIST -->

        <section class="tasks-section">

            <div class="section-title">

                <h2>
                    My Tasks
                </h2>


                <button
                    onclick="deleteCompleted()"
                    class="clear-btn"
                >
                    Clear Completed
                </button>

            </div>


            <div id="taskList"></div>


            <div
                id="emptyMessage"
                class="empty"
            >

                <div>
                    📝
                </div>

                <h3>
                    No tasks yet
                </h3>

                <p>
                    Add your first task and start being productive!
                </p>

            </div>

        </section>


        <!-- FOOTER -->

        <footer>

            <p>
                TaskSphere © 2026
            </p>

            <p>
                Name: <strong>Kaneimozhi</strong>
                |
                Register No: <strong>212224040147</strong>
            </p>

        </footer>

    </div>


    <script src="script.js"></script>

</body>

</html>
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:root {
    --primary: #6366f1;
    --primary-dark: #4f46e5;
    --background: #f5f7ff;
    --card: #ffffff;
    --text: #1f2937;
    --muted: #6b7280;
    --border: #e5e7eb;
    --shadow: 0 8px 25px rgba(0, 0, 0, 0.06);
}

body {
    font-family: Arial, sans-serif;
    background: var(--background);
    color: var(--text);
    min-height: 100vh;
    transition: 0.3s;
}

body.dark {
    --background: #111827;
    --card: #1f2937;
    --text: #f9fafb;
    --muted: #9ca3af;
    --border: #374151;
}

.app {
    width: 92%;
    max-width: 1200px;
    margin: auto;
    padding: 35px 0;
}

/* HEADER */

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
}

.header h1 {
    font-size: 40px;
    letter-spacing: -1px;
}

.header h1 span {
    color: var(--primary);
}

.header p {
    color: var(--muted);
    margin-top: 8px;
}

.theme-btn {
    width: 48px;
    height: 48px;
    border: none;
    border-radius: 50%;
    background: var(--card);
    box-shadow: var(--shadow);
    cursor: pointer;
    font-size: 21px;
}

/* STATISTICS */

.stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 18px;
    margin-bottom: 25px;
}

.stat-card {
    background: var(--card);
    padding: 22px;
    border-radius: 16px;
    display: flex;
    align-items: center;
    gap: 16px;
    box-shadow: var(--shadow);
}

.stat-icon {
    font-size: 30px;
}

.stat-card h3 {
    font-size: 26px;
}

.stat-card p {
    color: var(--muted);
    font-size: 13px;
    margin-top: 4px;
}

/* TASK FORM */

.task-form {
    background: var(--card);
    padding: 20px;
    border-radius: 16px;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr auto;
    gap: 10px;
    box-shadow: var(--shadow);
    margin-bottom: 20px;
}

input,
select {
    width: 100%;
    padding: 13px;
    border: 1px solid var(--border);
    border-radius: 9px;
    background: var(--card);
    color: var(--text);
    outline: none;
    font-size: 14px;
}

input:focus,
select:focus {
    border-color: var(--primary);
}

.add-btn {
    border: none;
    background: var(--primary);
    color: white;
    padding: 13px 20px;
    border-radius: 9px;
    cursor: pointer;
    font-weight: bold;
    white-space: nowrap;
}

.add-btn:hover {
    background: var(--primary-dark);
}

/* SEARCH */

.search-box {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

.search-box input {
    flex: 1;
}

/* PROGRESS */

.progress-container {
    background: var(--card);
    padding: 20px;
    border-radius: 16px;
    margin-bottom: 25px;
    box-shadow: var(--shadow);
}

.progress-info {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
    font-weight: bold;
}

.progress-bar {
    height: 12px;
    background: var(--border);
    border-radius: 20px;
    overflow: hidden;
}

#progressBar {
    height: 100%;
    width: 0%;
    background: var(--primary);
    border-radius: 20px;
    transition: width 0.4s ease;
}

/* SECTION */

.section-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}

.clear-btn {
    border: none;
    background: transparent;
    color: #ef4444;
    cursor: pointer;
    font-weight: bold;
}

/* TASK CARD */

.task {
    background: var(--card);
    padding: 18px;
    margin-bottom: 12px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    gap: 15px;
    box-shadow: var(--shadow);
    border-left: 5px solid var(--primary);
}

.task.completed {
    opacity: 0.6;
}

.check {
    width: 21px;
    height: 21px;
    cursor: pointer;
}

.task-content {
    flex: 1;
}

.task-title {
    font-size: 17px;
    font-weight: bold;
}

.task.completed .task-title {
    text-decoration: line-through;
}

.task-info {
    display: flex;
    gap: 8px;
    margin-top: 8px;
    flex-wrap: wrap;
}

.badge {
    padding: 5px 10px;
    border-radius: 20px;
    font-size: 12px;
    background: #eef2ff;
    color: #4f46e5;
}

.high {
    background: #fee2e2;
    color: #dc2626;
}

.medium {
    background: #fef3c7;
    color: #b45309;
}

.low {
    background: #dcfce7;
    color: #15803d;
}

.task-actions {
    display: flex;
    gap: 7px;
}

.action-btn {
    border: none;
    padding: 8px 10px;
    border-radius: 8px;
    cursor: pointer;
}

.edit {
    background: #e5e7eb;
}

.delete {
    background: #fee2e2;
    color: #dc2626;
}

/* EMPTY */

.empty {
    text-align: center;
    padding: 60px 20px;
    color: var(--muted);
}

.empty div {
    font-size: 50px;
    margin-bottom: 10px;
}

.empty h3 {
    color: var(--text);
    margin-bottom: 6px;
}

/* FOOTER */

footer {
    text-align: center;
    color: var(--muted);
    margin-top: 40px;
    padding: 25px;
    line-height: 1.8;
}

/* RESPONSIVE */

@media (max-width: 1000px) {

    .stats {
        grid-template-columns: repeat(2, 1fr);
    }

    .task-form {
        grid-template-columns: 1fr 1fr;
    }

    .add-btn {
        grid-column: span 2;
    }
}

@media (max-width: 600px) {

    .app {
        width: 94%;
        padding: 20px 0;
    }

    .header h1 {
        font-size: 30px;
    }

    .header p {
        font-size: 13px;
    }

    .stats {
        grid-template-columns: 1fr 1fr;
    }

    .stat-card {
        padding: 16px;
    }

    .stat-icon {
        font-size: 24px;
    }

    .task-form {
        grid-template-columns: 1fr;
    }

    .add-btn {
        grid-column: auto;
    }

    .search-box {
        flex-direction: column;
    }

    .task {
        align-items: flex-start;
    }

    .task-actions {
        flex-direction: column;
    }

    .section-title {
        align-items: flex-start;
        gap: 10px;
    }
}

```javascript
// Store tasks in Local Storage
let tasks = JSON.parse(localStorage.getItem("taskSphereTasks")) || [];


// ===============================
// ADD TASK
// ===============================

function addTask() {

    const input = document.getElementById("taskInput");
    const category = document.getElementById("category").value;
    const priority = document.getElementById("priority").value;
    const dueDate = document.getElementById("dueDate").value;

    const title = input.value.trim();

    if (title === "") {
        alert("Please enter a task!");
        return;
    }

    const task = {
        id: Date.now(),
        title: title,
        category: category,
        priority: priority,
        dueDate: dueDate,
        completed: false
    };

    tasks.push(task);

    saveTasks();

    input.value = "";
    document.getElementById("dueDate").value = "";

    displayTasks();
}


// ===============================
// DISPLAY TASKS
// ===============================

function displayTasks() {

    const list = document.getElementById("taskList");
    const empty = document.getElementById("emptyMessage");

    const search = document
        .getElementById("searchInput")
        .value
        .toLowerCase();

    const filter = document.getElementById("filter").value;
    const sort = document.getElementById("sort").value;


    let filteredTasks = tasks.filter(task => {

        const matchesSearch =
            task.title.toLowerCase().includes(search);

        if (!matchesSearch) {
            return false;
        }

        if (filter === "pending") {
            return !task.completed;
        }

        if (filter === "completed") {
            return task.completed;
        }

        if (filter === "high") {
            return task.priority === "High";
        }

        return true;
    });


    // ===============================
    // SORT TASKS
    // ===============================

    if (sort === "newest") {

        filteredTasks.sort(
            (a, b) => b.id - a.id
        );

    }


    if (sort === "oldest") {

        filteredTasks.sort(
            (a, b) => a.id - b.id
        );

    }


    if (sort === "priority") {

        const priorityValue = {
            High: 3,
            Medium: 2,
            Low: 1
        };

        filteredTasks.sort(
            (a, b) =>
                priorityValue[b.priority] -
                priorityValue[a.priority]
        );
    }


    list.innerHTML = "";


    // Empty message

    if (filteredTasks.length === 0) {

        empty.style.display = "block";

    } else {

        empty.style.display = "none";

    }


    // ===============================
    // CREATE TASK CARDS
    // ===============================

    filteredTasks.forEach(task => {

        const div = document.createElement("div");

        div.className =
            "task " +
            (task.completed ? "completed" : "");


        const dateText = task.dueDate
            ? `📅 ${task.dueDate}`
            : "📅 No deadline";


        div.innerHTML = `

            <input
                type="checkbox"
                class="check"
                ${task.completed ? "checked" : ""}
                onchange="toggleTask(${task.id})"
            >


            <div class="task-content">

                <div class="task-title">
                    ${task.title}
                </div>


                <div class="task-info">

                    <span class="badge">
                        📌 ${task.category}
                    </span>


                    <span class="badge ${task.priority.toLowerCase()}">
                        ${task.priority}
                    </span>


                    <span class="badge">
                        ${dateText}
                    </span>

                </div>

            </div>


            <div class="task-actions">

                <button
                    class="action-btn edit"
                    onclick="editTask(${task.id})"
                    title="Edit Task"
                >
                    ✏️
                </button>


                <button
                    class="action-btn delete"
                    onclick="deleteTask(${task.id})"
                    title="Delete Task"
                >
                    🗑️
                </button>

            </div>
        `;


        list.appendChild(div);

    });


    updateStats();
}


// ===============================
// COMPLETE / UNCOMPLETE TASK
// ===============================

function toggleTask(id) {

    const task = tasks.find(
        task => task.id === id
    );


    if (task) {

        task.completed =
            !task.completed;

    }


    saveTasks();

    displayTasks();
}


// ===============================
// DELETE TASK
// ===============================

function deleteTask(id) {

    const confirmDelete =
        confirm("Are you sure you want to delete this task?");


    if (!confirmDelete) {
        return;
    }


    tasks = tasks.filter(
        task => task.id !== id
    );


    saveTasks();

    displayTasks();
}


// ===============================
// EDIT TASK
// ===============================

function editTask(id) {

    const task = tasks.find(
        task => task.id === id
    );


    if (!task) {
        return;
    }


    const newTitle =
        prompt(
            "Edit your task:",
            task.title
        );


    if (newTitle === null) {
        return;
    }


    if (newTitle.trim() === "") {

        alert("Task cannot be empty!");

        return;
    }


    task.title =
        newTitle.trim();


    saveTasks();

    displayTasks();
}


// ===============================
// CLEAR COMPLETED TASKS
// ===============================

function deleteCompleted() {

    const completedCount =
        tasks.filter(
            task => task.completed
        ).length;


    if (completedCount === 0) {

        alert("There are no completed tasks.");

        return;
    }


    const confirmClear =
        confirm(
            "Clear all completed tasks?"
        );


    if (!confirmClear) {
        return;
    }


    tasks = tasks.filter(
        task => !task.completed
    );


    saveTasks();

    displayTasks();
}


// ===============================
// UPDATE STATISTICS
// ===============================

function updateStats() {

    const total = tasks.length;


    const completed =
        tasks.filter(
            task => task.completed
        ).length;


    const pending =
        total - completed;


    const percentage =
        total === 0
            ? 0
            : Math.round(
                (completed / total) * 100
            );


    document.getElementById(
        "totalTasks"
    ).textContent = total;


    document.getElementById(
        "pendingTasks"
    ).textContent = pending;


    document.getElementById(
        "completedTasks"
    ).textContent = completed;


    document.getElementById(
        "progress"
    ).textContent =
        percentage + "%";


    document.getElementById(
        "progressText"
    ).textContent =
        percentage + "%";


    document.getElementById(
        "progressBar"
    ).style.width =
        percentage + "%";
}


// ===============================
// SAVE TASKS
// ===============================

function saveTasks() {

    localStorage.setItem(
        "taskSphereTasks",
        JSON.stringify(tasks)
    );
}


// ===============================
// DARK MODE
// ===============================

document.getElementById(
    "themeBtn"
).onclick = function () {

    document.body.classList.toggle("dark");


    if (
        document.body.classList.contains("dark")
    ) {

        this.textContent = "☀️";

        localStorage.setItem(
            "taskSphereTheme",
            "dark"
        );

    } else {

        this.textContent = "🌙";

        localStorage.setItem(
            "taskSphereTheme",
            "light"
        );
    }
};


// ===============================
// LOAD SAVED THEME
// ===============================

if (
    localStorage.getItem(
        "taskSphereTheme"
    ) === "dark"
) {

    document.body.classList.add("dark");

    document.getElementById(
        "themeBtn"
    ).textContent = "☀️";
}


// ===============================
// ENTER KEY TO ADD TASK
// ===============================

document.getElementById(
    "taskInput"
).addEventListener(
    "keydown",
    function(event) {

        if (event.key === "Enter") {

            addTask();

        }

    }
);


// ===============================
// INITIAL DISPLAY
// ===============================

displayTasks();
```


## OUTPUT

<img width="1878" height="916" alt="Screenshot 2026-08-19 084857" src="https://github.com/user-attachments/assets/c2a7c624-ba74-4a9b-aaf9-cfb62f7f662a" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
