.calculator {
    max-width: 300px;
    margin: 20px auto;
    padding: 20px;
    background: #f0f0f0;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

.display {
    background: #fff;
    padding: 20px;
    margin-bottom: 10px;
    text-align: right;
    font-size: 24px;
    border-radius: 5px;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    padding: 15px;
    font-size: 18px;
    border: none;
    border-radius: 5px;
    background: #fff;
    cursor: pointer;
}

button:hover {
    background: #ddd;
}

.clear {
    background: #ff4444;
    color: white;
}

.equals {
    background: #4CAF50;
    color: white;
}
