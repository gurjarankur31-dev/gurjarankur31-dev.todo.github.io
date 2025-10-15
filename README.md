<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Add Task</title>
<style>
  body { font-family: "Poppins", sans-serif; display:flex; flex-direction:column; align-items:center; padding:20px; }
  input, button { padding:10px; margin:5px; border-radius:8px; font-size:16px; }
  button { cursor:pointer; }
  a { margin-top:20px; font-size:18px; text-decoration:none; color:blue; }
</style>
</head>
<body>

<h1>Add Task</h1>
<input type="text" id="taskInput" placeholder="Enter your task">
<input type="datetime-local" id="dateTimeInput">
<button onclick="addTask()">Save Task</button>
<a href="tasks.html">See Your Tasks</a>

<script>
function addTask() {
    const taskText = document.getElementById("taskInput").value.trim();
    const taskDateTime = document.getElementById("dateTimeInput").value;

    if(!taskText || !taskDateTime) { alert("Enter both task and date/time!"); return; }

    const task = { id: Date.now(), text: taskText, dateTime: taskDateTime, completed: false };
    let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
    tasks.push(task);
    localStorage.setItem("tasks", JSON.stringify(tasks));

    document.getElementById("taskInput").value = "";
    document.getElementById("dateTimeInput").value = "";
    alert("Task saved! Click 'See Your Tasks' to view all.");
}
</script>

</body>
</html>
