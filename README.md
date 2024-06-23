
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ToDoList-Project</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap"
 rel="stylesheet">
 <style>
:root{
    --primary:#EA40A4;
    --business:#3A82EE;
    --personal:var(--primary);
    --light:#EEE;
    --grey:#888;
    --dark:#313154;
    --danger:#ff5b57;
    --shadow:0 1px 3px rgba(0,0,0,0.1);
    --business-glow:0px 0px 4px rgba(58,130,238,0.75);
    --personal-glow:0px 0px 4px rgba(234,64,164,0.75);
}
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'montserrat','sans-serif';
 }
  input:not([type="radio"]):not([type="checkbox"]),button{
    appearance: none;
    border: none;
    outline: none;
    background:none ;
    cursor:  pointer;
    font-weight: bold;
    font-size: 1.35rem;
 }
 body{
    background: var(--light);
    color: var(--dark);
 }
 section{
    margin-top: 2rem;
    margin-bottom: 2rem;
    padding-left: 1.5rem;
    padding-right: 1.5rem;
 }
 h3{
    color: var(--dark);
    font-size: 1rem;
    font-weight: 400;
    margin-bottom: 0.5rem;
 }
 h4{
   color: var(--grey); 
   font-size: 0.875rem;
   font-weight: 700;
   margin-bottom: 0.5rem;
 }
 .greeting.title{
    display: flex;
 }
 .greeting.title input{
    margin-left: 0.5rem;
    flex: 1 1 0%;
    min-width: 0;
    
 }
 .greeting.title,.greeting.title input{
    color: var(--dark);
    font-size: 1.5rem;
    font-weight: 700;
 }
 .create-todo input[type="text"]
 {
    display: block;
    width: 20%;
    font-size: 1.125rem;
    padding: 1rem 1.5rem;
    color: var(--dark);
    background-color: #FFF;
    border-radius: 0.5rem;
    box-shadow: var(--shadow);
    margin-bottom: 1.5rem;
    
 }
 .options{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    grid-gap: 1rem;
    margin-bottom: 1.5rem;
 }
 .create-todo .options label{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 1.0rem;
    background-color: #FFF;
    border-radius: 0.5rem;
    width: 40%;
    column-gap: 0.5rem;
    box-shadow: var(--shadow);
    cursor: pointer;
 }
 input[type="radio"],
 input[type="checkbox"]{
    display: none;
 }
 .bubble{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 2px solid var(--business);
    box-shadow: var(--personal-glow);
 }
 .bubble.personal{
    border-color: var(--personal);
    box-shadow: var(--personal-glow);
 }
 .bubble::after{
    content: "";
    display: block;
    opacity: 0;
    width: 0px;
    height: 0px;
    background-color: var(--business);
    box-shadow: var(--business-glow);
    border-radius: 50%;
    transition: 0.2s ease-in-out;
 }
 .bubble.personal::after{
    background-color: var(--personal);
    box-shadow: var(--personal-glow);
 }
 input:checked ~ .bubble::after{
    width: 10px;
    height: 10px;
    opacity: 1;
 }
 .create-todo.options label div{
    color: var(--dark);
    font-size: 1.125rem;
    margin-top: 1rem;
 }
 .create-todo input[type="submit"]{
    display: block;
    width: 20%;
    font-size:1.125rem ;
    padding: 1rem 1.5rem;
    color:#FFF;
    background-color: var(--primary);
    border-radius: 0.5rem;
    box-shadow: var(--personal-glow);
    cursor: pointer;
    transition: 0.2s ease-in-out;
 }
 .create-todo input[type="submit"]:hover{
    opacity: 0.75;
 }
 .todo-list.list{
    margin: 1rem 0;
 }
 .todo-list .todo-item{
    display: flex;
    align-items: center;
    background-color: #FFF;
    padding: 1rem;
    width: 40%;
    
    border-radius: 0.5rem;
    box-shadow: var(--shadow);
    margin-bottom: 1rem;
 }
 .todo-item label{
    display: block;
    margin-right: 1rem;
    cursor: pointer;
 }
 .todo-item.todo-content{
    flex:1 1 0%;
 }
 .todo-item.todo-content
 {
    color: var(--dark);
    font-size: 1.125rem;
 }
 .todo-item.actions{
    display: flex;
    align-items: center;
 }
 .todo-item.actions button{
    display: block;
    padding: 0.5rem;
    border-radius: 0.25rem;
    color: #FFF;
    cursor: pointer;
    transition: 0.2s ease-in-out;
 }
 .actions button:hover{
    opacity: 0.75;
 }
 .edit{
    margin-right: 0.5rem;
    background-color: var(--primary);
    padding: 0.4rem;
    border-radius: 0.25rem;
 }
.delete{
    background-color: var(--danger);
    padding: 0.4rem;
    border-radius: 0.25rem;
 }
.todo-item.done input{
    text-decoration: line-through;
    color: var(--grey);
}
 </style>
</head>
<body>
    <main class="app">
        <section class="greeting">
            <h2 class="title">
                What's up,<input type="text" id="name" placeholder="Name here">
            </h2>
        </section>
<section class="create-todo">
    <h3>CREATE A TODO</h3>
    <form id="new-todo-form">
        <h4>What's on your todo list?</h4>
        <input type="text"name="content"
        id="content"
        placeholder="e.g make a video"/>
        <h4>Pick a category</h4>
        <div class="options">
            <label>
                <input type="radio"
                name="category"
                id="category1"
                value="business"/>
                <span class="bubble business"></span>
                <div>Business</div>
            </label>
            <label>
                <input type="radio"
                name="category"
                id="category2"
                value="personal"/>
                <span class="bubble personal"></span>
                <div>Personal</div>
            </label>
        </div>
        <input type="submit" value="Add todo">
    </form>
</section>
<section class="todo-list">
    <h3>TODO LIST</h3>
    <div class="list"id="todo-list">
        <!--div class="todo-item done">
            <label>
                <input type="checkbox" />
                <span class="bubble business"></span>
            </label>
            <div class="todo-content">
                <input type="text"value="Make a video" readonly/>
            </div>
            <div class="actions">
                <button class="edit">Edit</button>
                <button class="delete">Delete</button>
            </div>
        </div>
        <div class="todo-item">
            <label>
                <input type="checkbox" />
                <span class="bubble business"></span>
            </label>
            <div class="todo-content">
                <input type="text"value="Make a video" readonly/>
            </div>
            <div class="actions">
                <button class="edit">Edit</button>
                <button class="delete">Delete</button>
            </div>
        </div!-->
    </div>
</section>
    </main>
    <script>
        window.addEventListener('load',()=>{
            todos=JSON.parse(localStorage.getItem('todos'))||[]
       const nameInput=document.querySelector('#name');
       const newTodoForm=document.querySelector('#new-todo-form')
       
       const username=localStorage.getItem('username')||'';

       nameInput.value=username;
       nameInput.addEventListener('change',e=>{
        localStorage.setItem('username',e.target.value);
       })
       newTodoForm.addEventListener('submit',e=>{
        e.preventDefault();

        const todo={
            content:e.target.elements.content.value,
            category:e.target.elements.category.value,
            done:false,
            createAdt:new Date().getTime()
           
        }
        todos.push(todo);
        localStorage.setItem('todos',JSON.stringify(todos));

        e.target.reset();
        DisplayTodos();
       })
       DisplayTodos();
    
    })
    function DisplayTodos()
    {
        const todoList=document.querySelector('#todo-list');

        todoList.innerHTML='';

        todos.forEach(todo=>{
            const todoItem=document.createElement('div');
            todoItem.classList.add('todo-item');
             
            const label=document.createElement('label');
            const input=document.createElement('input');
            const span=document.createElement('span');
            const content=document.createElement('div');
            const actions=document.createElement('div');
            const edit=document.createElement('button');
            const deleteButton=document.createElement('button');
            

            input.type='checkbox';
            input.checked=todo.done;
            span.classList.add('bubble');

            if(todo.category=='personal')
            {
                span.classList.add('personal');
            }
            else
            {
                span.classList.add('personal');
            }
            content.classList.add('todo-content');
            actions.classList.add('actions');
            edit.classList.add('edit');
            deleteButton.classList.add('delete');
            
            content.innerHTML=`<input type="text" value="${todo.content}"
            readonly>`;
            edit.innerHTML='Edit';
            deleteButton.innerHTML='Delete';

            label.appendChild(input);
            label.appendChild(span);
            actions.appendChild(edit);
            actions.appendChild(deleteButton);
            todoItem.appendChild(label);
            todoItem.appendChild(content);
            todoItem.appendChild(actions);

            todoList.appendChild(todoItem);

            if(todo.done)
            {
                todoItem.classList.add('done');
            }
           input.addEventListener('click',e=>{
            todo.done=e.target.checked;
            localStorage.setItem('todos',JSON.stringify(todos));

            if(todo.done)
            {
                todoItem.classList.add('done');
            }
            else
            {
                todoItem.classList.remove('done');
            }

            DisplayTodos();
           })

           edit.addEventListener('click',e=>{
            const input=content.querySelector('input');
            input.removeAttribute('readonly');
            input.focus();
            input.addEventListener('blur',e=>{
                input.setAttribute('readonly',true);
                todo.content=e.target.value;
                localStorage.setItem('todos',JSON.stringify(todos));

                DisplayTodos();
            })
           })

 deleteButton.addEventListener('click',e=>{
    todos=todos.filter(t=>t !=todo);
    localStorage.setItem('todos',JSON.stringify(todos));
    DisplayTodos();
 })



        })
    }
    </script>
</body>
</html>
