# Pet-Activity-Tracker
A pet activity tracker is a smart device designed to monitor your pet's daily movements, exercise, and health. 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pet Activity Tracker</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary:Black;
            --secondary: #FD79A8;
            --accent: #00CEC9;
            --dark: #2D3436;
            --light: #F5F6FA;
            --text: #636E72;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: var(--light);
            color: var(--dark);
            min-height: 100vh;
        }

        .app-container {
            display: grid;
            grid-template-columns: 280px 1fr 200px;
            min-height: 100vh;
            max-width: 1600px;
            margin: 0 auto;
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.1);
            background: white;
        }

        /* Sidebar */
        .sidebar {
            background: linear-gradient(180deg, var(--primary) 0%, #6A5ACD 100%);
            color: white;
            padding: 25px;
            overflow-y: auto;
            position: relative;
        }

        /* Registration Panel */
        .registration-panel {
            background: white;
            padding: 25px;
            border-left: 1px solid #e0e0e0;
            display: flex;
            flex-direction: column;
        }

        .registration-panel h3 {
            font-size: 18px;
            margin-bottom: 20px;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .registration-panel h3 i {
            color: var(--accent);
        }

        .registration-list {
            list-style: none;
        }

        .registration-item {
            padding: 10px 0;
            border-bottom: 1px solid #e0e0e0;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .registration-item:last-child {
            border-bottom: none;
        }

        .registration-item i {
            color: var(--accent);
        }

        .logo {
            display: flex;
            align-items: center;
            margin-bottom: 30px;
            gap: 12px;
        }

        .university-logo {
            width: 60px;
            height: 60px;
            display: flex;
            align-items: center;
        }

        .university-logo img {
            width: 100%;
            height: auto;
            object-fit: contain;
        }

        .logo-text {
            display: flex;
            flex-direction: column;
        }

        .logo-text-primary {
            font-size: 18px;
            font-weight: 700;
            color: white;
            line-height: 1.2;
        }

        .logo-text-secondary {
            font-size: 10px;
            color: white;
            font-weight: 400;
            margin-top: 3px;
        }

        .history-section {
            margin-bottom: 30px;
        }

        .history-section h3 {
            font-size: 18px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .history-section h3 i {
            color: var(--accent);
        }

        .history-list {
            list-style: none;
        }

        .history-item {
            padding: 10px 15px;
            margin-bottom: 8px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .history-item:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateX(5px);
        }

        .history-item i {
            color: var(--accent);
        }

        /* Add Pet Form */
        .add-pet-form {
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 12px;
            margin-top: 30px;
        }

        .add-pet-form h3 {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .add-pet-form input, .add-pet-form select {
            width: 100%;
            padding: 10px;
            margin-bottom: 12px;
            border: none;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.9);
        }

        .add-pet-form button {
            width: 100%;
            padding: 10px;
            background: var(--accent);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .add-pet-form button:hover {
            background: #3DBDB4;
            transform: translateY(-2px);
        }

        /* Main Content */
        .main-content {
            display: flex;
            flex-direction: column;
            padding: 25px;
            background: var(--light);
        }

        /* Chat Container */
        .chat-container {
            flex: 1;
            display: flex;
            flex-direction: column;
            background: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            overflow: hidden;
        }

        .chat-header {
            padding: 20px;
            background: var(--primary);
            color: white;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .chat-header i {
            font-size: 24px;
            color: var(--accent);
        }

        .chat-header h2 {
            font-size: 20px;
        }

        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .message {
            max-width: 80%;
            padding: 12px 18px;
            border-radius: 18px;
            line-height: 1.4;
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .bot-message {
            background: #F0F4F8;
            border-bottom-left-radius: 5px;
            align-self: flex-start;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
        }

        .user-message {
            background: var(--primary);
            color: white;
            border-bottom-right-radius: 5px;
            align-self: flex-end;
        }

        .activity-message {
            background: white;
            border: 1px solid #E0E6ED;
            border-radius: 12px;
            padding: 15px;
            margin-top: 5px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
        }

        .pet-status {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
        }

        .pet-status img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent);
        }

        .pet-status h4 {
            font-size: 18px;
        }

        .activity-tag {
            display: inline-block;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
            margin-top: 8px;
        }

        .sleeping { background: #A78BFA; color: white; }
        .walking { background: #4ADE80; color: white; }
        .eating { background: #F59E0B; color: white; }
        .playing { background: #F97316; color: white; }
        .idle { background: #94A3B8; color: white; }

        .chat-input {
            display: flex;
            padding: 15px;
            background: #F8FAFC;
            border-top: 1px solid #E2E8F0;
        }

        .chat-input input {
            flex: 1;
            padding: 12px 15px;
            border: 1px solid #E2E8F0;
            border-radius: 25px;
            outline: none;
            font-family: 'Poppins', sans-serif;
            transition: all 0.3s;
        }

        .chat-input input:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(138, 43, 226, 0.2);
        }

        .chat-input button {
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            margin-left: 10px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .chat-input button:hover {
            background: #7B1FA2;
            transform: scale(1.05);
        }

        /* Pet Activity Stats */
        .pet-stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-top: 10px;
        }

        .stat-item {
            background: #F8FAFC;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
        }

        .stat-value {
            font-weight: 700;
            font-size: 16px;
            color: var(--primary);
        }

        .stat-label {
            font-size: 12px;
            color: #64748B;
        }

        /* Responsive */
        @media (max-width: 1024px) {
            .app-container {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                position: fixed;
                top: 0;
                left: -280px;
                width: 280px;
                height: 100vh;
                z-index: 100;
                transition: left 0.3s ease;
            }

            .registration-panel {
                position: fixed;
                top: 0;
                right: -200px;
                width: 200px;
                height: 100vh;
                z-index: 100;
                transition: right 0.3s ease;
            }

            .sidebar.active {
                left: 0;
            }

            .registration-panel.active {
                right: 0;
            }

            .main-content {
                padding: 15px;
            }

            .message {
                max-width: 90%;
            }
        }

        /* Toggle buttons for mobile */
        .sidebar-toggle {
            display: none;
            position: fixed;
            top: 20px;
            left: 20px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            z-index: 101;
            cursor: pointer;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .registration-toggle {
            display: none;
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            z-index: 101;
            cursor: pointer;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        @media (max-width: 1024px) {
            .sidebar-toggle, .registration-toggle {
                display: flex;
                align-items: center;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <button class="sidebar-toggle" id="sidebarToggle">
        <i class="fas fa-bars"></i>
    </button>
    <button class="registration-toggle" id="registrationToggle">
        <i class="fas fa-id-card"></i>
    </button>

    <div class="app-container">
        <aside class="sidebar" id="sidebar">
            <div class="logo">
                <div class="university-logo">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQT25cdNVUin8QJungLOZvAOrRm9XjEkZFZpTPX0i5mLEhGpmLv-WIExDLcyPyxilMRYNw&usqp=CAU" alt="LPU Logo">
                </div>
                <div class="logo-text">
                    <div class="logo-text-primary">Pet Activity Tracker</div>
                    <div class="logo-text-secondary">Done by LPU Students</div>
                </div>
            </div>

            <div class="history-section">
                <h3><i class="fas fa-history"></i> Recently Added Pet's.</h3>
                <ul class="history-list" id="historyList">
                    <!-- History items will be added here dynamically -->
                    <li style="color: #ccc;">No searches yet</li>
                </ul>
            </div>

            <div class="add-pet-form">
                <h3><i class="fas fa-plus-circle"></i> Add Your Pet</h3>
                <input type="text" id="petNameInput" placeholder="Pet Name" required>
                <select id="petTypeInput">
                    <option value="dog">🐕 Dog</option>
                    <option value="cat">🐈 Cat</option>
                    <option value="bird">🐦 Bird</option>
                    <option value="rabbit">🐇 Rabbit</option>
                </select>
                <button id="addPetBtn"><i class="fas fa-paper-plane"></i> Add Pet</button>
            </div>
        </aside>

        <main class="main-content">
            <div class="chat-container">
                <div class="chat-header">
                    <i class="fas fa-robot"></i>
                    <h2>Pet Activity Tracker.</h2>
                </div>
                
                <div class="chat-messages" id="chatMessages">
                    <div class="message bot-message">
                        🐾 Welcome to <strong>Pet Activity Tracker</strong>! I'm your Pet Activity Tracker. 
                        You can ask me things like:<br><br>
                        • "What is Pet doing?"<br>
                        • "How is Pet?"<br>
                        • "Show me my pets"
                    </div>
                </div>
                
                <div class="chat-input">
                    <input type="text" id="userInput" placeholder="Ask about your pet..." autocomplete="off">
                    <button id="sendButton"><i class="fas fa-paper-plane"></i></button>
                </div>
            </div>
        </main>

        <aside class="registration-panel" id="registrationPanel">
            <h3><i class="fas fa-id-card"></i> Registration Numbers</h3>
            <ul class="registration-list">
                <li class="registration-item">
                    <i class="fas fa-user"></i> 12313271(Ajay)
                </li>
                <li class="registration-item">
                    <i class="fas fa-user"></i> 12301238(Ekshin)
                </li>
                <li class="registration-item">
                    <i class="fas fa-user"></i> 12304981(Tarak)
                </li>
            </ul>
        </aside>
    </div>

    <script>
        // Pet database (stored in localStorage)
        let petsDatabase = JSON.parse(localStorage.getItem('petsDatabase')) || [
            {
                id: '1',
                name: 'Max',
                type: 'dog',
                image: 'https://images.unsplash.com/photo-1586671267731-da2cf3ceeb80?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80',
                activity: {
                    type: 'sleeping',
                    lastUpdated: new Date().toISOString()
                }
            },
            {
                id: '2',
                name: 'Bella',
                type: 'cat',
                image: 'https://images.unsplash.com/photo-1544568100-847a948585b9?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80',
                activity: {
                    type: 'playing',
                    lastUpdated: new Date().toISOString()
                }
            }
        ];

        // Search history (not stored in localStorage anymore)
        let searchHistory = [];

        // Possible activities
        const activities = [
            { type: "sleeping", emoji: "😴", message: "is sleeping peacefully" },
            { type: "walking", emoji: "🐕", message: "is out for a walk" },
            { type: "eating", emoji: "🍖", message: "is eating food" },
            { type: "playing", emoji: "🎾", message: "is playing with toys" },
            { type: "idle", emoji: "🐾", message: "is relaxing" }
        ];

        // DOM Elements
        const chatMessages = document.getElementById('chatMessages');
        const userInput = document.getElementById('userInput');
        const sendButton = document.getElementById('sendButton');
        const historyList = document.getElementById('historyList');
        const addPetBtn = document.getElementById('addPetBtn');
        const petNameInput = document.getElementById('petNameInput');
        const petTypeInput = document.getElementById('petTypeInput');
        const sidebar = document.getElementById('sidebar');
        const sidebarToggle = document.getElementById('sidebarToggle');
        const registrationPanel = document.getElementById('registrationPanel');
        const registrationToggle = document.getElementById('registrationToggle');

        // Initialize the app
        function init() {
            // Clear any existing history items
            historyList.innerHTML = '<li style="color: #ccc;">No searches yet</li>';
            
            // Set up event listeners
            sendButton.addEventListener('click', sendMessage);
            userInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') sendMessage();
            });
            addPetBtn.addEventListener('click', addNewPet);
            sidebarToggle.addEventListener('click', toggleSidebar);
            registrationToggle.addEventListener('click', toggleRegistrationPanel);
            
            // Simulate pet activity changes
            setInterval(updatePetActivities, 5000);
        }

        // Send message function
        function sendMessage() {
            const message = userInput.value.trim();
            if (!message) return;
            
            // Add user message to chat
            addMessage(message, 'user');
            
            // Process the message
            processUserMessage(message);
            
            // Clear input
            userInput.value = '';
        }

        // Add message to chat
        function addMessage(text, sender, pet = null) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message');
            messageDiv.classList.add(sender === 'user' ? 'user-message' : 'bot-message');
            
            if (pet) {
                // If we have pet data, create a richer message
                const activity = activities.find(a => a.type === pet.activity.type);
                messageDiv.innerHTML = `
                    ${text}
                    <div class="activity-message">
                        <div class="pet-status">
                            <img src="${pet.image}" alt="${pet.name}" class="pet-avatar">
                            <h4>${pet.name} ${activity.message} ${activity.emoji}</h4>
                        </div>
                        <span class="activity-tag ${pet.activity.type}">
                            ${pet.activity.type.toUpperCase()}
                        </span>
                        <div class="pet-stats">
                            <div class="stat-item">
                                <div class="stat-value">${new Date(pet.activity.lastUpdated).toLocaleTimeString()}</div>
                                <div class="stat-label">Last Active</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-value">${pet.type.toUpperCase()}</div>
                                <div class="stat-label">Pet Type</div>
                            </div>
                        </div>
                    </div>
                `;
            } else {
                messageDiv.textContent = text;
            }
            
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        // Process user message
        function processUserMessage(message) {
            const lowerMessage = message.toLowerCase();
            
            // Check for specific commands
            if (lowerMessage.includes('add a new pet') || lowerMessage.includes('add pet')) {
                const nameMatch = lowerMessage.match(/named (\w+)/);
                if (nameMatch) {
                    const petName = nameMatch[1];
                    petNameInput.value = petName;
                    addMessage(`Great! I see you want to add ${petName}. Please fill out the form on the left to complete the process.`, 'bot');
                } else {
                    addMessage('Please use the form on the left to add a new pet, or tell me "Add a new pet named [name]".', 'bot');
                }
                return;
            }
            
            if (lowerMessage.includes('show my pets') || lowerMessage.includes('list pets')) {
                if (petsDatabase.length === 0) {
                    addMessage("You don't have any pets yet. Use the form on the left to add one!", 'bot');
                } else {
                    let petsList = "Here are your pets:\n\n";
                    petsDatabase.forEach(pet => {
                        petsList += `• ${pet.name} (${pet.type})\n`;
                    });
                    addMessage(petsList, 'bot');
                }
                return;
            }
            
            // Check if asking about a pet's activity
            const petNames = petsDatabase.map(pet => pet.name.toLowerCase());
            const mentionedPet = petNames.find(name => 
                lowerMessage.includes(name) || 
                lowerMessage.includes(`what is ${name} doing`) ||
                lowerMessage.includes(`how is ${name}`)
            );
            
            if (mentionedPet) {
                const pet = petsDatabase.find(p => p.name.toLowerCase() === mentionedPet);
                
                // Add to search history (only for current session)
                if (!searchHistory.includes(pet.name)) {
                    searchHistory.unshift(pet.name);
                    if (searchHistory.length > 5) searchHistory.pop();
                    updateHistoryDisplay();
                }
                
                // Show pet activity
                setTimeout(() => {
                    addMessage(`Here's ${pet.name}'s current status:`, 'bot', pet);
                }, 800);
            } else {
                // No pet recognized - show help
                setTimeout(() => {
                    if (petsDatabase.length > 0) {
                        const petNames = petsDatabase.map(p => p.name).join(', ');
                        addMessage(`I don't recognize that pet. Try asking about ${petNames}. Or say "Add a new pet named [name]" to register a new pet.`, 'bot');
                    } else {
                        addMessage(`You don't have any pets yet. Use the form on the left to add one!`, 'bot');
                    }
                }, 800);
            }
        }

        // Add new pet
        function addNewPet() {
            const name = petNameInput.value.trim();
            const type = petTypeInput.value;
            const image = `https://source.unsplash.com/200x200/?${type}`;
            
            if (!name) {
                alert('Please enter a pet name');
                return;
            }
            
            // Check if pet already exists
            if (petsDatabase.some(pet => pet.name.toLowerCase() === name.toLowerCase())) {
                alert('A pet with this name already exists');
                return;
            }
            
            // Create new pet
            const newPet = {
                id: Date.now().toString(),
                name,
                type,
                image,
                activity: {
                    type: activities[Math.floor(Math.random() * activities.length)].type,
                    lastUpdated: new Date().toISOString()
                }
            };
            
            // Add to database
            petsDatabase.push(newPet);
            localStorage.setItem('petsDatabase', JSON.stringify(petsDatabase));
            
            // Clear form
            petNameInput.value = '';
            
            // Show confirmation
            addMessage(`Successfully added ${name} to your pets! � You can now ask about ${name}.`, 'bot');
        }

        // Update pet activities randomly
        function updatePetActivities() {
            petsDatabase.forEach(pet => {
                if (Math.random() > 0.7) { // 30% chance to change activity
                    pet.activity = {
                        type: activities[Math.floor(Math.random() * activities.length)].type,
                        lastUpdated: new Date().toISOString()
                    };
                }
            });
            localStorage.setItem('petsDatabase', JSON.stringify(petsDatabase));
        }

        // Update history display
        function updateHistoryDisplay() {
            historyList.innerHTML = '';
            
            if (searchHistory.length === 0) {
                const item = document.createElement('li');
                item.textContent = 'No searches yet';
                item.style.color = '#ccc';
                historyList.appendChild(item);
                return;
            }
            
            searchHistory.forEach(petName => {
                const pet = petsDatabase.find(p => p.name === petName);
                const item = document.createElement('li');
                item.classList.add('history-item');
                
                if (pet) {
                    item.innerHTML = `
                        <i class="fas fa-${pet.type}"></i>
                        ${pet.name}
                    `;
                } else {
                    item.innerHTML = `
                        <i class="fas fa-paw"></i>
                        ${petName}
                    `;
                }
                
                item.addEventListener('click', () => {
                    userInput.value = `What is ${petName} doing?`;
                    userInput.focus();
                });
                
                historyList.appendChild(item);
            });
        }

        // Toggle sidebar on mobile
        function toggleSidebar() {
            sidebar.classList.toggle('active');
        }

        // Toggle registration panel on mobile
        function toggleRegistrationPanel() {
            registrationPanel.classList.toggle('active');
        }

        // Initialize the app when DOM is loaded
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
