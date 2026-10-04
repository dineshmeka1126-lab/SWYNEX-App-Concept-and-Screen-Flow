# Student Task Planner App

## 1. App Overview

The Student Task Planner is a simple productivity application designed to help students organize their daily academic activities.

Students can add assignments, set deadlines, view their tasks, and track completed activities.

## 2. Target User

The target users are college and university students who want a simple way to manage their assignments, study tasks, and deadlines.

## 3. Main Features

* Add new tasks
* Set task deadlines
* View upcoming tasks
* Mark tasks as completed
* Track task progress
* View profile and app settings

## 4. App Screens

### Screen 1 – Welcome / Login

The user can enter the app through a simple login or continue to the main dashboard.

### Screen 2 – Dashboard

Shows today's tasks, upcoming deadlines, and task completion progress.

### Screen 3 – Add Task

Allows the user to enter:

* Task name
* Description
* Due date
* Priority

### Screen 4 – My Tasks

Displays all pending and completed tasks.

### Screen 5 – Task Details

Shows complete information about a selected task and allows the user to mark it as completed.

### Screen 6 – Profile / Settings

Allows the user to view their profile and manage basic application settings.

## 5. Navigation Flow

Welcome/Login
↓
Dashboard
↓
Add Task
↓
My Tasks
↓
Task Details
↓
Profile / Settings

The user can return to the Dashboard from the main screens using the navigation menu.

## 6. Expected Result

The app provides students with a simple and organized way to manage academic tasks and deadlines.

## 7. Learning Outcome

Through this task, I learned how to define a target user, plan application screens, organize navigation flow, and create a basic app concept before development.
# SWYNEX-App-Concept-and-Screen-Flow
A simple Student Task Planner app concept designed to help students organize daily tasks, assignments, deadlines, and track their progress through an easy-to-use screen flow.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Task Planner</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f4f6f8;
            color: #222;
        }

        header {
            background: #2563eb;
            color: white;
            padding: 20px;
            text-align: center;
        }

        header h1 {
            margin-bottom: 5px;
        }

        nav {
            background: white;
            display: flex;
            justify-content: center;
            gap: 10px;
            padding: 12px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        nav button {
            border: none;
            background: #e5e7eb;
            padding: 10px 16px;
            border-radius: 6px;
            cursor: pointer;
        }

        nav button:hover {
            background: #2563eb;
            color: white;
        }

        .container {
            max-width: 900px;
            margin: 30px auto;
            padding: 20px;
        }

        .screen {
            display: none;
        }

        .active {
            display: block;
        }

        .card {
            background: white;
            padding: 25px;
            margin-bottom: 20px;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .stat {
            background: #eff6ff;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        .stat h2 {
            color: #2563eb;
        }

        input,
        textarea,
        select {
            width: 100%;
            padding: 12px;
            margin: 8px 0 15px;
            border: 1px solid #ccc;
            border-radius: 6px;
        }

        .btn {
            background: #2563eb;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 6px;
            cursor: pointer;
        }

        .btn:hover {
            background: #1d4ed8;
        }

        .task {
            background: #f9fafb;
            padding: 15px;
            margin: 10px 0;
            border-left: 5px solid #2563eb;
            border-radius: 6px;
        }

        .task.completed {
            border-left-color: #16a34a;
            opacity: 0.7;
        }

        .task button {
            margin-top: 10px;
            padding: 7px 12px;
            border: none;
            background: #16a34a;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }

        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            background: #111827;
            color: white;
        }

        @media (max-width: 600px) {
            .stats {
                grid-template-columns: 1fr;
            }

            nav {
                flex-wrap: wrap;
            }
        }
    </style>
</head>

<body>

<header>
    <h1>Student Task Planner</h1>
    <p>Manage your academic tasks easily</p>
</header>

<nav>
    <button onclick="showScreen('dashboard')">Dashboard</button>
    <button onclick="showScreen('addTask')">Add Task</button>
    <button onclick="showScreen('tasks')">My Tasks</button>
    <button onclick="showScreen('profile')">Profile</button>
</nav>

<div class="container">

    <!-- Dashboard -->
    <section id="dashboard" class="screen active">

        <div class="card">
            <h2>Welcome, Student! 👋</h2>
            <p>Stay organized and complete your academic tasks on time.</p>

            <div class="stats">
                <div class="stat">
                    <h2 id="totalTasks">0</h2>
                    <p>Total Tasks</p>
                </div>

                <div class="stat">
                    <h2 id="pendingTasks">0</h2>
                    <p>Pending</p>
                </div>

                <div class="stat">
                    <h2 id="completedTasks">0</h2>
                    <p>Completed</p>
                </div>
            </div>
        </div>

        <div class="card">
            <h2>Today's Tasks</h2>
            <div id="dashboardTasks">
                <p>No tasks added yet.</p>
            </div>
        </div>

    </section>

    <!-- Add Task -->
    <section id="addTask" class="screen">

        <div class="card">
            <h2>Add New Task</h2>

            <label>Task Name</label>
            <input type="text" id="taskName" placeholder="Enter task name">

            <label>Description</label>
            <textarea id="taskDescription"
                      placeholder="Enter task description"></textarea>

            <label>Due Date</label>
            <input type="date" id="taskDate">

            <label>Priority</label>
            <select id="taskPriority">
                <option value="Low">Low</option>
                <option value="Medium">Medium</option>
                <option value="High">High</option>
            </select>

            <button class="btn" onclick="addTask()">Add Task</button>
        </div>

    </section>

    <!-- My Tasks -->
    <section id="tasks" class="screen">

        <div class="card">
            <h2>My Tasks</h2>
            <div id="taskList">
                <p>No tasks available.</p>
            </div>
        </div>

    </section>

    <!-- Task Details -->
    <section id="details" class="screen">

        <div class="card">
            <h2>Task Details</h2>
            <div id="taskDetails">
                <p>Select a task to view its details.</p>
            </div>
        </div>

    </section>

    <!-- Profile -->
    <section id="profile" class="screen">

        <div class="card">
            <h2>Profile</h2>

            <p><strong>Name:</strong> Student</p>
            <p><strong>Role:</strong> College Student</p>
            <p><strong>Purpose:</strong> Manage academic tasks</p>

            <br>

            <h3>Application Settings</h3>
            <p>✔ Task reminders</p>
            <p>✔ Deadline tracking</p>
            <p>✔ Task completion tracking</p>
        </div>

    </section>

</div>

<footer>
    SWYNEX Task 1 | Student Task Planner
</footer>

<script>

    let tasks = [];

    function showScreen(screenName) {

        let screens = document.querySelectorAll(".screen");

        screens.forEach(function(screen) {
            screen.classList.remove("active");
        });

        document.getElementById(screenName).classList.add("active");

        if (screenName === "tasks") {
            displayTasks();
        }

        if (screenName === "dashboard") {
            updateDashboard();
        }
    }


    function addTask() {

        let name = document.getElementById("taskName").value;
        let description = document.getElementById("taskDescription").value;
        let date = document.getElementById("taskDate").value;
        let priority = document.getElementById("taskPriority").value;

        if (name === "" || date === "") {
            alert("Please enter task name and due date.");
            return;
        }

        let task = {
            name: name,
            description: description,
            date: date,
            priority: priority,
            completed: false
        };

        tasks.push(task);

        alert("Task added successfully!");

        document.getElementById("taskName").value = "";
        document.getElementById("taskDescription").value = "";
        document.getElementById("taskDate").value = "";

        showScreen("tasks");
    }


    function displayTasks() {

        let taskList = document.getElementById("taskList");

        if (tasks.length === 0) {
            taskList.innerHTML = "<p>No tasks available.</p>";
            return;
        }

        taskList.innerHTML = "";

        tasks.forEach(function(task, index) {

            let div = document.createElement("div");

            div.className = "task";

            if (task.completed) {
                div.classList.add("completed");
            }

            div.innerHTML = `
                <h3>${task.name}</h3>
                <p>${task.description}</p>
                <p><strong>Due:</strong> ${task.date}</p>
                <p><strong>Priority:</strong> ${task.priority}</p>

                <button onclick="completeTask(${index})">
                    ${task.completed ? "Completed" : "Mark as Complete"}
                </button>

                <button onclick="viewDetails(${index})">
                    View Details
                </button>
            `;

            taskList.appendChild(div);
        });
    }


    function completeTask(index) {

        tasks[index].completed = true;

        displayTasks();
        updateDashboard();
    }


    function viewDetails(index) {

        let task = tasks[index];

        document.getElementById("taskDetails").innerHTML = `
            <h3>${task.name}</h3>
            <p><strong>Description:</strong> ${task.description}</p>
            <p><strong>Due Date:</strong> ${task.date}</p>
            <p><strong>Priority:</strong> ${task.priority}</p>
            <p><strong>Status:</strong>
                ${task.completed ? "Completed ✅" : "Pending ⏳"}
            </p>
        `;

        showScreen("details");
    }


    function updateDashboard() {

        let total = tasks.length;

        let completed = tasks.filter(function(task) {
            return task.completed;
        }).length;

        let pending = total - completed;

        document.getElementById("totalTasks").innerText = total;
        document.getElementById("completedTasks").innerText = completed;
        document.getElementById("pendingTasks").innerText = pending;

        let dashboard = document.getElementById("dashboardTasks");

        if (tasks.length === 0) {
            dashboard.innerHTML = "<p>No tasks added yet.</p>";
            return;
        }

        dashboard.innerHTML = "";

        tasks.slice(0, 5).forEach(function(task) {

            dashboard.innerHTML += `
                <div class="task">
                    <h3>${task.name}</h3>
                    <p>Due: ${task.date}</p>
                    <p>Priority: ${task.priority}</p>
                </div>
            `;

        });
    }

</script>

</body>
</html>
