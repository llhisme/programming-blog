---
title: "JavaScript Cơ Bản #4: DOM Manipulation và Events"
date: 2024-02-05
draft: false
description: "Học cách sử dụng JavaScript để tương tác với HTML DOM và xử lý events"
tags: ["javascript", "dom", "events", "html", "tương tác"]
categories: ["JavaScript"]
series: ["JavaScript Cơ Bản"]
series_order: 4
featureimage: "img/blowfish_logo.png"
showTableOfContents: true
---

## DOM là gì?

**DOM** (Document Object Model) là cách trình duyệt biểu diễn trang HTML dưới dạng cây đối tượng. JavaScript có thể sử dụng DOM để:

- Thay đổi nội dung HTML
- Thay đổi thuộc tính HTML
- Thay đổi CSS styles
- Thêm/xóa HTML elements
- Phản ứng với HTML events

### Cấu trúc DOM Tree

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Example</title>
</head>
<body>
    <div id="container">
        <h1>Tiêu đề</h1>
        <p class="content">Đoạn văn</p>
    </div>
</body>
</html>
```

Cấu trúc DOM:
```
Document
└── html
    ├── head
    │   └── title
    │       └── "DOM Example"
    └── body
        └── div#container
            ├── h1
            │   └── "Tiêu đề"
            └── p.content
                └── "Đoạn văn"
```

## Selecting Elements (Chọn phần tử)

### 1. Các phương thức cơ bản

```javascript
// Chọn theo ID
const element = document.getElementById('myId');

// Chọn theo class (trả về NodeList)
const elements = document.getElementsByClassName('myClass');

// Chọn theo tag name
const paragraphs = document.getElementsByTagName('p');

// Chọn theo CSS selector (phần tử đầu tiên)
const firstDiv = document.querySelector('div');
const specificElement = document.querySelector('#myId .myClass');

// Chọn tất cả theo CSS selector
const allDivs = document.querySelectorAll('div');
const allButtons = document.querySelectorAll('button.btn');
```

### 2. Ví dụ thực tế

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>DOM Selection</title>
    <style>
        .highlight { background-color: yellow; }
        .hidden { display: none; }
        .red-text { color: red; }
    </style>
</head>
<body>
    <div id="main-container">
        <h1 id="main-title">Tiêu đề chính</h1>
        <p class="content">Đoạn văn thứ nhất</p>
        <p class="content special">Đoạn văn đặc biệt</p>
        <ul id="item-list">
            <li class="item">Mục 1</li>
            <li class="item">Mục 2</li>
            <li class="item">Mục 3</li>
        </ul>
        <button id="btn-highlight">Highlight</button>
        <button id="btn-hide">Ẩn/Hiện</button>
    </div>

    <script>
        // Chọn các phần tử
        const mainTitle = document.getElementById('main-title');
        const contentParagraphs = document.getElementsByClassName('content');
        const allItems = document.querySelectorAll('.item');
        const specialParagraph = document.querySelector('.content.special');
        const buttons = document.querySelectorAll('button');

        console.log('Main title:', mainTitle.textContent);
        console.log('Number of content paragraphs:', contentParagraphs.length);
        console.log('All items:', allItems);

        // Lặp qua NodeList
        allItems.forEach((item, index) => {
            console.log(`Item ${index + 1}:`, item.textContent);
        });

        // Chuyển HTMLCollection thành Array
        const contentArray = Array.from(contentParagraphs);
        contentArray.forEach(p => {
            console.log('Content:', p.textContent);
        });
    </script>
</body>
</html>
```

## Manipulating Content (Thay đổi nội dung)

### 1. Text Content

```javascript
// innerHTML - có thể chứa HTML
element.innerHTML = '<strong>Nội dung mới</strong>';

// textContent - chỉ text thuần
element.textContent = 'Nội dung text thuần';

// innerText - text hiển thị (tính cả CSS)
element.innerText = 'Text hiển thị';

// outerHTML - thay thế cả element
element.outerHTML = '<div>Element mới</div>';
```

### 2. Attributes

```javascript
// Lấy attribute
const value = element.getAttribute('data-value');
const id = element.id; // Shorthand cho getAttribute('id')

// Đặt attribute
element.setAttribute('data-value', '123');
element.id = 'new-id'; // Shorthand

// Xóa attribute
element.removeAttribute('data-value');

// Kiểm tra attribute tồn tại
if (element.hasAttribute('data-value')) {
    console.log('Có attribute data-value');
}

// Dataset API (HTML5 data attributes)
element.dataset.userId = '123'; // data-user-id="123"
console.log(element.dataset.userId); // "123"
```

### 3. CSS Styles

```javascript
// Thay đổi style trực tiếp
element.style.color = 'red';
element.style.backgroundColor = 'yellow';
element.style.fontSize = '20px';

// Thay đổi nhiều style cùng lúc
Object.assign(element.style, {
    color: 'blue',
    fontSize: '18px',
    padding: '10px'
});

// CSS Classes
element.classList.add('new-class');
element.classList.remove('old-class');
element.classList.toggle('active'); // Thêm nếu chưa có, xóa nếu có
element.classList.contains('active'); // true/false

// className (cách cũ)
element.className = 'class1 class2';
element.className += ' class3';
```

## Creating and Modifying Elements

### 1. Tạo elements mới

```javascript
// Tạo element
const newDiv = document.createElement('div');
const newParagraph = document.createElement('p');

// Đặt nội dung và thuộc tính
newDiv.textContent = 'Div mới';
newDiv.id = 'new-div';
newDiv.classList.add('container');

newParagraph.innerHTML = '<strong>Đoạn văn mới</strong>';

// Tạo text node
const textNode = document.createTextNode('Text thuần');
```

### 2. Thêm elements vào DOM

```javascript
// appendChild - thêm vào cuối
parentElement.appendChild(newDiv);

// insertBefore - thêm trước element khác
parentElement.insertBefore(newDiv, existingElement);

// insertAdjacentElement
element.insertAdjacentElement('beforebegin', newDiv); // Trước element
element.insertAdjacentElement('afterbegin', newDiv);  // Đầu element
element.insertAdjacentElement('beforeend', newDiv);   // Cuối element
element.insertAdjacentElement('afterend', newDiv);    // Sau element

// insertAdjacentHTML - thêm HTML string
element.insertAdjacentHTML('beforeend', '<p>New paragraph</p>');
```

### 3. Xóa elements

```javascript
// Xóa element (cách mới)
element.remove();

// Xóa element (cách cũ)
parentElement.removeChild(element);

// Xóa tất cả children
element.innerHTML = '';

// Thay thế element
parentElement.replaceChild(newElement, oldElement);
```

## Event Handling (Xử lý sự kiện)

### 1. Các cách thêm event listener

```javascript
// addEventListener (khuyến nghị)
button.addEventListener('click', function() {
    console.log('Button clicked!');
});

// Arrow function
button.addEventListener('click', () => {
    console.log('Button clicked with arrow function!');
});

// Named function
function handleClick() {
    console.log('Button clicked with named function!');
}
button.addEventListener('click', handleClick);

// HTML attribute (không khuyến nghị)
// <button onclick="handleClick()">Click me</button>

// Property assignment
button.onclick = function() {
    console.log('Button clicked via property!');
};
```

### 2. Event Object

```javascript
button.addEventListener('click', function(event) {
    console.log('Event type:', event.type);
    console.log('Target element:', event.target);
    console.log('Current target:', event.currentTarget);
    console.log('Mouse position:', event.clientX, event.clientY);
    
    // Ngăn hành vi mặc định
    event.preventDefault();
    
    // Ngăn event bubbling
    event.stopPropagation();
});
```

### 3. Các loại events phổ biến

```javascript
// Mouse events
element.addEventListener('click', handleClick);
element.addEventListener('dblclick', handleDoubleClick);
element.addEventListener('mousedown', handleMouseDown);
element.addEventListener('mouseup', handleMouseUp);
element.addEventListener('mouseover', handleMouseOver);
element.addEventListener('mouseout', handleMouseOut);
element.addEventListener('mousemove', handleMouseMove);

// Keyboard events
document.addEventListener('keydown', function(e) {
    console.log('Key pressed:', e.key);
    console.log('Key code:', e.keyCode);
});

document.addEventListener('keyup', handleKeyUp);

// Form events
form.addEventListener('submit', function(e) {
    e.preventDefault(); // Ngăn form submit
    console.log('Form submitted');
});

input.addEventListener('input', function(e) {
    console.log('Input value:', e.target.value);
});

input.addEventListener('change', handleInputChange);
input.addEventListener('focus', handleFocus);
input.addEventListener('blur', handleBlur);

// Window events
window.addEventListener('load', function() {
    console.log('Page fully loaded');
});

window.addEventListener('resize', function() {
    console.log('Window resized');
});

window.addEventListener('scroll', function() {
    console.log('Page scrolled');
});
```

## Bài tập thực hành

### Bài 1: Todo List Application

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
        }
        
        .container {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 30px;
        }
        
        .input-section {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        #todo-input {
            flex: 1;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        
        #todo-input:focus {
            outline: none;
            border-color: #4CAF50;
        }
        
        #add-btn {
            padding: 12px 20px;
            background: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        
        #add-btn:hover {
            background: #45a049;
        }
        
        .filters {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            justify-content: center;
        }
        
        .filter-btn {
            padding: 8px 16px;
            border: 2px solid #ddd;
            background: white;
            border-radius: 5px;
            cursor: pointer;
        }
        
        .filter-btn.active {
            background: #4CAF50;
            color: white;
            border-color: #4CAF50;
        }
        
        #todo-list {
            list-style: none;
            padding: 0;
        }
        
        .todo-item {
            display: flex;
            align-items: center;
            padding: 15px;
            margin-bottom: 10px;
            background: #f9f9f9;
            border-radius: 5px;
            border-left: 4px solid #4CAF50;
        }
        
        .todo-item.completed {
            opacity: 0.6;
            border-left-color: #ccc;
        }
        
        .todo-item.completed .todo-text {
            text-decoration: line-through;
        }
        
        .todo-checkbox {
            margin-right: 15px;
            transform: scale(1.2);
        }
        
        .todo-text {
            flex: 1;
            font-size: 16px;
        }
        
        .todo-actions {
            display: flex;
            gap: 10px;
        }
        
        .edit-btn, .delete-btn {
            padding: 5px 10px;
            border: none;
            border-radius: 3px;
            cursor: pointer;
            font-size: 12px;
        }
        
        .edit-btn {
            background: #2196F3;
            color: white;
        }
        
        .delete-btn {
            background: #f44336;
            color: white;
        }
        
        .stats {
            text-align: center;
            margin-top: 20px;
            padding: 15px;
            background: #e8f5e8;
            border-radius: 5px;
        }
        
        .empty-state {
            text-align: center;
            padding: 40px;
            color: #666;
            font-style: italic;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📝 Todo List</h1>
        
        <div class="input-section">
            <input type="text" id="todo-input" placeholder="Nhập công việc cần làm...">
            <button id="add-btn">Thêm</button>
        </div>
        
        <div class="filters">
            <button class="filter-btn active" data-filter="all">Tất cả</button>
            <button class="filter-btn" data-filter="active">Chưa hoàn thành</button>
            <button class="filter-btn" data-filter="completed">Đã hoàn thành</button>
        </div>
        
        <ul id="todo-list"></ul>
        
        <div class="stats" id="stats"></div>
    </div>

    <script>
        // Todo List Application
        class TodoApp {
            constructor() {
                this.todos = JSON.parse(localStorage.getItem('todos')) || [];
                this.currentFilter = 'all';
                this.nextId = this.todos.length > 0 ? Math.max(...this.todos.map(t => t.id)) + 1 : 1;
                
                this.initializeElements();
                this.attachEventListeners();
                this.render();
            }
            
            initializeElements() {
                this.todoInput = document.getElementById('todo-input');
                this.addBtn = document.getElementById('add-btn');
                this.todoList = document.getElementById('todo-list');
                this.filterBtns = document.querySelectorAll('.filter-btn');
                this.stats = document.getElementById('stats');
            }
            
            attachEventListeners() {
                // Thêm todo
                this.addBtn.addEventListener('click', () => this.addTodo());
                this.todoInput.addEventListener('keypress', (e) => {
                    if (e.key === 'Enter') this.addTodo();
                });
                
                // Filter buttons
                this.filterBtns.forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        this.setFilter(e.target.dataset.filter);
                    });
                });
            }
            
            addTodo() {
                const text = this.todoInput.value.trim();
                if (!text) {
                    alert('Vui lòng nhập nội dung công việc!');
                    return;
                }
                
                const todo = {
                    id: this.nextId++,
                    text: text,
                    completed: false,
                    createdAt: new Date().toISOString()
                };
                
                this.todos.push(todo);
                this.todoInput.value = '';
                this.saveTodos();
                this.render();
                
                // Animation effect
                this.todoInput.style.transform = 'scale(0.95)';
                setTimeout(() => {
                    this.todoInput.style.transform = 'scale(1)';
                }, 150);
            }
            
            toggleTodo(id) {
                const todo = this.todos.find(t => t.id === id);
                if (todo) {
                    todo.completed = !todo.completed;
                    this.saveTodos();
                    this.render();
                }
            }
            
            deleteTodo(id) {
                if (confirm('Bạn có chắc muốn xóa công việc này?')) {
                    this.todos = this.todos.filter(t => t.id !== id);
                    this.saveTodos();
                    this.render();
                }
            }
            
            editTodo(id) {
                const todo = this.todos.find(t => t.id === id);
                if (!todo) return;
                
                const newText = prompt('Sửa nội dung:', todo.text);
                if (newText !== null && newText.trim()) {
                    todo.text = newText.trim();
                    this.saveTodos();
                    this.render();
                }
            }
            
            setFilter(filter) {
                this.currentFilter = filter;
                
                // Update active filter button
                this.filterBtns.forEach(btn => {
                    btn.classList.toggle('active', btn.dataset.filter === filter);
                });
                
                this.render();
            }
            
            getFilteredTodos() {
                switch (this.currentFilter) {
                    case 'active':
                        return this.todos.filter(t => !t.completed);
                    case 'completed':
                        return this.todos.filter(t => t.completed);
                    default:
                        return this.todos;
                }
            }
            
            render() {
                const filteredTodos = this.getFilteredTodos();
                
                // Clear list
                this.todoList.innerHTML = '';
                
                if (filteredTodos.length === 0) {
                    this.renderEmptyState();
                } else {
                    filteredTodos.forEach(todo => {
                        this.renderTodoItem(todo);
                    });
                }
                
                this.renderStats();
            }
            
            renderTodoItem(todo) {
                const li = document.createElement('li');
                li.className = `todo-item ${todo.completed ? 'completed' : ''}`;
                li.innerHTML = `
                    <input type="checkbox" class="todo-checkbox" ${todo.completed ? 'checked' : ''}>
                    <span class="todo-text">${this.escapeHtml(todo.text)}</span>
                    <div class="todo-actions">
                        <button class="edit-btn">✏️ Sửa</button>
                        <button class="delete-btn">🗑️ Xóa</button>
                    </div>
                `;
                
                // Event listeners
                const checkbox = li.querySelector('.todo-checkbox');
                const editBtn = li.querySelector('.edit-btn');
                const deleteBtn = li.querySelector('.delete-btn');
                
                checkbox.addEventListener('change', () => this.toggleTodo(todo.id));
                editBtn.addEventListener('click', () => this.editTodo(todo.id));
                deleteBtn.addEventListener('click', () => this.deleteTodo(todo.id));
                
                this.todoList.appendChild(li);
            }
            
            renderEmptyState() {
                const emptyDiv = document.createElement('div');
                emptyDiv.className = 'empty-state';
                
                let message = '';
                switch (this.currentFilter) {
                    case 'active':
                        message = '🎉 Không có công việc nào chưa hoàn thành!';
                        break;
                    case 'completed':
                        message = '📝 Chưa có công việc nào được hoàn thành.';
                        break;
                    default:
                        message = '📝 Chưa có công việc nào. Hãy thêm công việc đầu tiên!';
                }
                
                emptyDiv.textContent = message;
                this.todoList.appendChild(emptyDiv);
            }
            
            renderStats() {
                const total = this.todos.length;
                const completed = this.todos.filter(t => t.completed).length;
                const active = total - completed;
                
                this.stats.innerHTML = `
                    <strong>Thống kê:</strong> 
                    ${total} tổng cộng | 
                    ${active} chưa hoàn thành | 
                    ${completed} đã hoàn thành
                    ${total > 0 ? ` (${Math.round(completed/total*100)}% hoàn thành)` : ''}
                `;
            }
            
            saveTodos() {
                localStorage.setItem('todos', JSON.stringify(this.todos));
            }
            
            escapeHtml(text) {
                const div = document.createElement('div');
                div.textContent = text;
                return div.innerHTML;
            }
        }
        
        // Khởi tạo ứng dụng khi DOM đã sẵn sàng
        document.addEventListener('DOMContentLoaded', () => {
            new TodoApp();
        });
    </script>
</body>
</html>
```

### Bài 2: Image Gallery với Lightbox

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        h1 {
            text-align: center;
            margin-bottom: 30px;
            color: #333;
        }
        
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .gallery-item:hover {
            transform: scale(1.05);
        }
        
        .gallery-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            display: block;
        }
        
        .gallery-item .overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.7);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .gallery-item:hover .overlay {
            opacity: 1;
        }
        
        /* Lightbox Styles */
        .lightbox {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .lightbox.active {
            display: flex;
        }
        
        .lightbox-content {
            position: relative;
            max-width: 90%;
            max-height: 90%;
        }
        
        .lightbox img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }
        
        .lightbox-close {
            position: absolute;
            top: -40px;
            right: 0;
            color: white;
            font-size: 30px;
            cursor: pointer;
            background: none;
            border: none;
        }
        
        .lightbox-nav {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(255,255,255,0.2);
            color: white;
            border: none;
            font-size: 24px;
            padding: 10px 15px;
            cursor: pointer;
            border-radius: 5px;
        }
        
        .lightbox-prev {
            left: -60px;
        }
        
        .lightbox-next {
            right: -60px;
        }
        
        .lightbox-info {
            position: absolute;
            bottom: -50px;
            left: 0;
            right: 0;
            color: white;
            text-align: center;
        }
        
        .controls {
            text-align: center;
            margin-bottom: 20px;
        }
        
        .controls button {
            margin: 0 10px;
            padding: 10px 20px;
            background: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        
        .controls button:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🖼️ Image Gallery</h1>
        
        <div class="controls">
            <button id="add-image-btn">Thêm ảnh</button>
            <button id="slideshow-btn">Slideshow</button>
            <button id="shuffle-btn">Xáo trộn</button>
        </div>
        
        <div class="gallery" id="gallery"></div>
        
        <!-- Lightbox -->
        <div class="lightbox" id="lightbox">
            <div class="lightbox-content">
                <button class="lightbox-close" id="lightbox-close">&times;</button>
                <button class="lightbox-nav lightbox-prev" id="lightbox-prev">&#8249;</button>
                <img id="lightbox-img" src="" alt="">
                <button class="lightbox-nav lightbox-next" id="lightbox-next">&#8250;</button>
                <div class="lightbox-info" id="lightbox-info"></div>
            </div>
        </div>
    </div>

    <script>
        class ImageGallery {
            constructor() {
                this.images = [
                    {
                        id: 1,
                        src: 'https://picsum.photos/400/300?random=1',
                        title: 'Phong cảnh 1',
                        description: 'Một khung cảnh thiên nhiên tuyệt đẹp'
                    },
                    {
                        id: 2,
                        src: 'https://picsum.photos/400/300?random=2',
                        title: 'Phong cảnh 2',
                        description: 'Cảnh đẹp hoàng hôn'
                    },
                    {
                        id: 3,
                        src: 'https://picsum.photos/400/300?random=3',
                        title: 'Phong cảnh 3',
                        description: 'Núi non hùng vĩ'
                    },
                    {
                        id: 4,
                        src: 'https://picsum.photos/400/300?random=4',
                        title: 'Phong cảnh 4',
                        description: 'Biển xanh trong vắt'
                    },
                    {
                        id: 5,
                        src: 'https://picsum.photos/400/300?random=5',
                        title: 'Phong cảnh 5',
                        description: 'Rừng cây xanh mướt'
                    },
                    {
                        id: 6,
                        src: 'https://picsum.photos/400/300?random=6',
                        title: 'Phong cảnh 6',
                        description: 'Thành phố về đêm'
                    }
                ];
                
                this.currentImageIndex = 0;
                this.isSlideshow = false;
                this.slideshowInterval = null;
                
                this.initializeElements();
                this.attachEventListeners();
                this.renderGallery();
            }
            
            initializeElements() {
                this.gallery = document.getElementById('gallery');
                this.lightbox = document.getElementById('lightbox');
                this.lightboxImg = document.getElementById('lightbox-img');
                this.lightboxInfo = document.getElementById('lightbox-info');
                this.lightboxClose = document.getElementById('lightbox-close');
                this.lightboxPrev = document.getElementById('lightbox-prev');
                this.lightboxNext = document.getElementById('lightbox-next');
                this.addImageBtn = document.getElementById('add-image-btn');
                this.slideshowBtn = document.getElementById('slideshow-btn');
                this.shuffleBtn = document.getElementById('shuffle-btn');
            }
            
            attachEventListeners() {
                // Lightbox controls
                this.lightboxClose.addEventListener('click', () => this.closeLightbox());
                this.lightboxPrev.addEventListener('click', () => this.previousImage());
                this.lightboxNext.addEventListener('click', () => this.nextImage());
                
                // Keyboard navigation
                document.addEventListener('keydown', (e) => {
                    if (this.lightbox.classList.contains('active')) {
                        switch(e.key) {
                            case 'Escape':
                                this.closeLightbox();
                                break;
                            case 'ArrowLeft':
                                this.previousImage();
                                break;
                            case 'ArrowRight':
                                this.nextImage();
                                break;
                        }
                    }
                });
                
                // Click outside to close
                this.lightbox.addEventListener('click', (e) => {
                    if (e.target === this.lightbox) {
                        this.closeLightbox();
                    }
                });
                
                // Control buttons
                this.addImageBtn.addEventListener('click', () => this.addRandomImage());
                this.slideshowBtn.addEventListener('click', () => this.toggleSlideshow());
                this.shuffleBtn.addEventListener('click', () => this.shuffleImages());
            }
            
            renderGallery() {
                this.gallery.innerHTML = '';
                
                this.images.forEach((image, index) => {
                    const galleryItem = document.createElement('div');
                    galleryItem.className = 'gallery-item';
                    galleryItem.innerHTML = `
                        <img src="${image.src}" alt="${image.title}" loading="lazy">
                        <div class="overlay">
                            <div>
                                <h3>${image.title}</h3>
                                <p>${image.description}</p>
                            </div>
                        </div>
                    `;
                    
                    galleryItem.addEventListener('click', () => this.openLightbox(index));
                    this.gallery.appendChild(galleryItem);
                });
            }
            
            openLightbox(index) {
                this.currentImageIndex = index;
                this.updateLightboxImage();
                this.lightbox.classList.add('active');
                document.body.style.overflow = 'hidden';
            }
            
            closeLightbox() {
                this.lightbox.classList.remove('active');
                document.body.style.overflow = 'auto';
                this.stopSlideshow();
            }
            
            updateLightboxImage() {
                const image = this.images[this.currentImageIndex];
                this.lightboxImg.src = image.src;
                this.lightboxImg.alt = image.title;
                this.lightboxInfo.innerHTML = `
                    <h3>${image.title}</h3>
                    <p>${image.description}</p>
                    <small>${this.currentImageIndex + 1} / ${this.images.length}</small>
                `;
            }
            
            previousImage() {
                this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length;
                this.updateLightboxImage();
            }
            
            nextImage() {
                this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
                this.updateLightboxImage();
            }
            
            addRandomImage() {
                const newId = Math.max(...this.images.map(img => img.id)) + 1;
                const randomNum = Math.floor(Math.random() * 1000) + 100;
                
                const newImage = {
                    id: newId,
                    src: `https://picsum.photos/400/300?random=${randomNum}`,
                    title: `Phong cảnh ${newId}`,
                    description: `Ảnh được thêm tự động số ${newId}`
                };
                
                this.images.push(newImage);
                this.renderGallery();
                
                // Scroll to new image
                setTimeout(() => {
                    const newItem = this.gallery.lastElementChild;
                    newItem.scrollIntoView({ behavior: 'smooth' });
                    newItem.style.animation = 'pulse 1s ease-in-out';
                }, 100);
            }
            
            shuffleImages() {
                // Fisher-Yates shuffle algorithm
                for (let i = this.images.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [this.images[i], this.images[j]] = [this.images[j], this.images[i]];
                }
                
                this.renderGallery();
                
                // Add shuffle animation
                const items = this.gallery.querySelectorAll('.gallery-item');
                items.forEach((item, index) => {
                    item.style.animation = `fadeIn 0.5s ease-in-out ${index * 0.1}s both`;
                });
            }
            
            toggleSlideshow() {
                if (this.isSlideshow) {
                    this.stopSlideshow();
                } else {
                    this.startSlideshow();
                }
            }
            
            startSlideshow() {
                if (!this.lightbox.classList.contains('active')) {
                    this.openLightbox(0);
                }
                
                this.isSlideshow = true;
                this.slideshowBtn.textContent = 'Dừng Slideshow';
                this.slideshowBtn.style.background = '#dc3545';
                
                this.slideshowInterval = setInterval(() => {
                    this.nextImage();
                }, 3000);
            }
            
            stopSlideshow() {
                this.isSlideshow = false;
                this.slideshowBtn.textContent = 'Slideshow';
                this.slideshowBtn.style.background = '#007bff';
                
                if (this.slideshowInterval) {
                    clearInterval(this.slideshowInterval);
                    this.slideshowInterval = null;
                }
            }
        }
        
        // CSS animations
        const style = document.createElement('style');
        style.textContent = `
            @keyframes pulse {
                0% { transform: scale(1); }
                50% { transform: scale(1.1); }
                100% { transform: scale(1); }
            }
            
            @keyframes fadeIn {
                from { opacity: 0; transform: translateY(20px); }
                to { opacity: 1; transform: translateY(0); }
            }
        `;
        document.head.appendChild(style);
        
        // Initialize gallery when DOM is ready
        document.addEventListener('DOMContentLoaded', () => {
            new ImageGallery();
        });
    </script>
</body>
</html>
```

## Event Delegation

```javascript
// Thay vì thêm event listener cho từng element
document.querySelectorAll('.button').forEach(button => {
    button.addEventListener('click', handleClick);
});

// Sử dụng event delegation (hiệu quả hơn)
document.addEventListener('click', function(e) {
    if (e.target.classList.contains('button')) {
        handleClick(e);
    }
});

// Ví dụ thực tế với dynamic content
const container = document.getElementById('container');

container.addEventListener('click', function(e) {
    if (e.target.classList.contains('delete-btn')) {
        // Xử lý xóa
        const item = e.target.closest('.item');
        item.remove();
    } else if (e.target.classList.contains('edit-btn')) {
        // Xử lý sửa
        const item = e.target.closest('.item');
        editItem(item);
    }
});
```

## Performance Tips

```javascript
// 1. Cache DOM queries
const button = document.getElementById('myButton'); // Tốt
// Thay vì gọi document.getElementById('myButton') nhiều lần

// 2. Batch DOM updates
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
    const div = document.createElement('div');
    div.textContent = `Item ${i}`;
    fragment.appendChild(div);
}
container.appendChild(fragment); // Chỉ 1 lần reflow

// 3. Debounce expensive operations
function debounce(func, wait) {
    let timeout;
    return function executedFunction(...args) {
        const later = () => {
            clearTimeout(timeout);
            func(...args);
        };
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
    };
}

const debouncedSearch = debounce(function(query) {
    // Expensive search operation
    console.log('Searching for:', query);
}, 300);

searchInput.addEventListener('input', (e) => {
    debouncedSearch(e.target.value);
});

// 4. Use requestAnimationFrame for animations
function animate() {
    // Animation code
    element.style.left = position + 'px';
    position += 1;
    
    if (position < 100) {
        requestAnimationFrame(animate);
    }
}
requestAnimationFrame(animate);
```

## Tổng kết

Trong bài này, chúng ta đã học:
- DOM là gì và cách JavaScript tương tác với HTML
- Các phương thức chọn elements
- Thay đổi nội dung, attributes và styles
- Tạo, thêm và xóa elements
- Xử lý events và event object
- Event delegation và performance tips
- Thực hành với Todo List và Image Gallery

DOM Manipulation là kỹ năng cốt lõi để tạo ra các trang web tương tác. Với kiến thức này, bạn có thể xây dựng các ứng dụng web động và thú vị.

Đây là bài cuối cùng trong series JavaScript cơ bản. Bạn đã có nền tảng vững chắc để tiếp tục học các framework như React, Vue.js hoặc khám phá Node.js cho backend development!