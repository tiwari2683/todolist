# todolist react
const Todo = () => {
    const [inputValue, setInputValue] = useState("");
    const [task, setTask] = useState([]);

    const handleInputChange = (value) => {
        setInputValue(value);
    };

    const handleFormSubmit = (event) => {
        event.preventDefault();
        if (!inputValue) return;
        if(task.includes(inputValue))  return;
        
        setTask((prevTask) => [...prevTask, inputValue]);
        setInputValue(""); 
    };

    return (
        <section className="todo-container">
            <header>
                <h1>TODO LIST</h1>
            </header>
            <section className="form">
                {/* Attach onSubmit to the form correctly */}
                <form onSubmit={handleFormSubmit}>
                    <div className="kuchv">
                        <input 
                            type="text"
                            className="todo-input"
                            autoComplete="off"
                            value={inputValue}
                            onChange={(event) => handleInputChange(event.target.value)}
                        />
                        <button type="submit" className="todo-btn">
                        Add Task
                    </button>
                    </div>
                    {/* Move the button inside the form */}
                    
                </form>
            </section>
            {/* Display tasks */}
            <ul className="task-list">
                {task.map((t, index) => (
                    <li key={index}>{t}</li>
                ))}
            </ul>
        </section>
    );
};

export default Todo;



#todocss

/* Todo.css */

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color:rgb(230, 225, 225);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.todo-container {
  margin-top: -15rem;
  text-align: center;
  padding: 20px;
  background-color: #267de7;
  border-radius: 10px;
  width: 300px;
  box-shadow: 8px 8px 8px rgba(0,0,0);
}

header h1 {
  font-size: 24px;
  color: rgb(237, 235, 235);
  margin-bottom: 20px;
}

.form {
  display: flex;
  align-items: center;
  justify-content: center;
}

.todo-input {
  width: 180px;
  padding: 8px;
  border-radius: 5px 0 0 5px;
  border: 2px;
  border-color: red;
  outline: none;
  font-size: 16px;
}

.todo-btn {
  padding: 8px;
  background-color: #502bc1;
  border: 2px;
  
  border-radius: 0 5px 5px 0;
  color: white;
  cursor: pointer;
  font-size: 17px;
  outline: none;
  transition: background-color 0.3s ease;
}

.todo-btn:hover {
  background-color: #b6315d;
}

.kuchv{
  display: inline;
}


