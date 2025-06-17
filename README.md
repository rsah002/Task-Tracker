<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task Tracker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f6fb;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
        }
        .container {
            background: #fff;
            margin-top: 40px;
            padding: 32px 24px 24px 24px;
            border-radius: 12px;
            box-shadow: 0 4px 24px rgba(0,0,0,0.08);
            width: 100%;
            max-width: 400px;
        }
        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 24px;
        }
        .task-input {
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
        }
        .task-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 16px;
        }
        .task-input button {
            padding: 10px 18px;
            background: #4f8cff;
            color: #fff;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            cursor: pointer;
            transition: background 0.2s;
        }
        .task-input button:hover {
            background: #2563eb;
        }
        ul#task-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        ul#task-list li {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: #f7f9fc;
            margin-bottom: 10px;
            padding: 10px 12px;
            border-radius: 6px;
            transition: background 0.2s;
        }
        ul#task-list li.completed span {
            text-decoration: line-through;
            color: #aaa;
        }
        .actions {
            display: flex;
            gap: 8px;
        }
        .actions button {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 16px;
            padding: 4px 8px;
            border-radius: 4px;
            transition: background 0.2s;
        }
        .actions .complete-btn {
            color: #22c55e;
        }
        .actions .delete-btn {
            color: #ef4444;
        }
        .actions .complete-btn:hover {
            background: #d1fae5;
        }
        .actions .delete-btn:hover {
            background: #fee2e2;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Task Tracker</h1>
        <div class="task-input">
            <input type="text" id="new-task" placeholder="Add a new task...">
            <button id="add-task-btn">Add</button>
        </div>
        <ul id="task-list"></ul>
    </div>
    <script>
        const taskInput = document.getElementById('new-task');
        const addTaskBtn = document.getElementById('add-task-btn');
        const taskList = document.getElementById('task-list');

        function createTaskElement(taskText) {
            const li = document.createElement('li');
            const span = document.createElement('span');
            span.textContent = taskText;
            li.appendChild(span);

            const actions = document.createElement('div');
            actions.className = 'actions';

            const completeBtn = document.createElement('button');
            completeBtn.className = 'complete-btn';
            completeBtn.title = 'Mark as complete';
            completeBtn.innerHTML = '✔️';
            completeBtn.onclick = function() {
                li.classList.toggle('completed');
            };

            const deleteBtn = document.createElement('button');
            deleteBtn.className = 'delete-btn';
            deleteBtn.title = 'Delete task';
            deleteBtn.innerHTML = '🗑️';
            deleteBtn.onclick = function() {
                li.remove();
            };

            actions.appendChild(completeBtn);
            actions.appendChild(deleteBtn);
            li.appendChild(actions);
            return li;
        }

        addTaskBtn.addEventListener('click', function() {
            const taskText = taskInput.value.trim();
            if (taskText) {
                const taskElement = createTaskElement(taskText);
                taskList.appendChild(taskElement);
                taskInput.value = '';
                taskInput.focus();
            }
        });

        taskInput.addEventListener('keydown', function(e) {
            if (e.key === 'Enter') {
                addTaskBtn.click();
            }
        });
    </script>
</body>
</html> 
