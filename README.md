                                        PROJECT DOCUMENTATION (TO-DO LIST)

PROJECT DESCRIPTION :
The To-Do List Application is a simple and interactive web application that allows users to keep track of their daily tasks. Users can add new tasks, mark them as completed, and remove tasks. The project showcases fundamental web development concepts using HTML for structure, CSS for styling, and JavaScript for functionality.

FEATURES :
Add Tasks: Users can input and add new tasks to their list.
Complete Tasks: Tasks can be marked as completed, visually distinguishing them from pending tasks.
Delete Tasks: Users can remove tasks from their list.

PROJECT STRUCTURE :
todo-list/
│
├── css/
│   └── styles.css         # CSS styles for the application
│
├── js/
│   └── script.js          # JavaScript functionality
│
├── index.html             # Main HTML file
│
└── README.md              # Project documentation


SETTING UP :
1.CLONE REPOSITORY LOCALLY : git clone "https://github.com/karthik-web16/internship-task1.git"

2.NAVIGATING TO THE PROJECT DIRECTORY : cd todo-list

3.ADDING HTML FILE IN DIRECTORY : touch index.html



                                 HTML, CSS, and JavaScript CODE WALK THROUGH                   

                                          HTML (index.html) :

<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>To-Do List App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<div class="container">
    <div class="todo-app">
        <h2>To-Do List <img src="icon.png"></h2>
        <div class="row">
            <input type="text" id="input-box" placeholder="Add your text">
            <button onclick="addTask()">Add</button>
        </div>
        <ul id="list-container">
            <!--<li class="checked">Task 1</li>
            <li>Task 2</li>
            <li>Task 3</li>-->
        </ul>
    </div>
</div>
<script src="script.js"></script>
</body>
</html>

                                          CSS (styles.css) :
 *{
    margin: 0;
    padding: 0;
    font-family: "poppins", sans-serif;
    box-sizing: border-box;
}
.container{
    width: 100%;
    min-height: 100vh;
    background: linear-gradient(135deg, #153677, #4e085f);
    padding: 10px;
}
.todo-app{
    width: 100%;
    max-width: 540px;
    background: #fff;
    margin: 100px auto 20px;
    padding: 40px 30px 70px;
    border-radius: 10px;
}
.todo-app h2{
    color: #002765;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
}
.todo-app h2 img{
    width: 30px;
    margin-left: 10px;
}
.row{
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #edeef0;
    border-radius: 30px;
    padding-left: 20px;
    margin-bottom: 25px;
}
input{
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    padding: 10px;
    font-weight: 14px;
}
button{
    border: none;
    outline: none;
    padding: 16px 50px;
    background: #ff5945;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    border-radius: 40px;
}
ul li{
    list-style: none;
    font-size: 17px;
    padding: 12px 8px 12px 50px;
    user-select: none;
    cursor: pointer;
    position: relative;
}
ul li::before{
    content: '';
    position: absolute;
    height: 28px;
    width: 28px;
    border-radius: 50%;
    background-image: url(unchecked.png);
    background-size: cover;
    background-position: center;
    top: 12px;
    left: 8px;
}
ul li.checked{
    color: #555;
    text-decoration: line-through;
}
ul li.checked::before{
    background-image: url(checked.png);
}
ul li span{
    position: absolute;
    right: 0;
    top: 5px;
    width: 40px;
    height: 40px;
    font-size: 22px;
    color: #555;
    line-height: 40px;
    text-align: center;
    border-radius: 50%;
}
ul li span:hover{
    background: #edeef0;
}

                                            JavaScript (script.js) :

const inputBox = document.getElementById("input-box");
const listContainer = document.getElementById("list-container");

function addTask(){
    if(inputBox.value==''){
        alert("you must write something!");
    }
    else{
        let li = document.createElement("li");
        li.innerHTML = inputBox.value;
        listContainer.appendChild(li);
        let span = document.createElement("span");
        span.innerHTML = "\u00d7";
        li.appendChild(span);
    }
    inputBox.value = "";
    saveData();
}

listContainer.addEventListener("click", function(e){
    if(e.target.tagName === "LI"){
        e.target.classList.toggle("checked");
        saveData();
    }
    else if(e.target.tagName === "SPAN"){
        e.target.parentElement.remove();
    }
}, false);

function saveData(){
    localStorage.setItem("data",listContainer.innerHTML)
}
function showTask(){
    listContainer.innerHTML = localStorage.getItem("data")
}
showTask();


NOTES :
1.The HTML provides the structure for the application, including input fields and buttons.
2.The CSS styles the application, making it visually appealing and responsive.
3.The JavaScript adds interactivity, allowing users to add, complete, and delete tasks.

CONCLUSION :
This documentation covers the essentials for setting up and using your To-Do List application. It serves as a guide for both users and contributors, making your project accessible and maintainable.






