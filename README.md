<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Chat Picture - अपनी तस्वीरें शेयर करें</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4edf5 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            color: #333;
        }
        
        header {
            background: linear-gradient(to right, #ff4d6d, #ff758c);
            color: white;
            padding: 1.5rem 2rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo i {
            font-size: 1.8rem;
        }
        
        .logo h1 {
            font-size: 1.8rem;
            font-weight: 700;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff8fa3, #ff4d6d);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        .container {
            display: flex;
            flex: 1;
            max-width: 1400px;
            margin: 0 auto;
            width: 100%;
            padding: 20px;
            gap: 20px;
        }
        
        .sidebar {
            width: 300px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            padding: 20px;
            display: flex;
            flex-direction: column;
        }
        
        .sidebar h2 {
            color: #ff4d6d;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }
        
        .chat-list {
            flex: 1;
            overflow-y: auto;
        }
        
        .chat-item {
            display: flex;
            align-items: center;
            padding: 12px;
            border-radius: 10px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .chat-item:hover {
            background: #f8f9fa;
        }
        
        .chat-item.active {
            background: #ffeef1;
            border-left: 4px solid #ff4d6d;
        }
        
        .chat-avatar {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: linear-gradient(135deg, #a5b4fc, #818cf8);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            margin-right: 12px;
        }
        
        .chat-info {
            flex: 1;
        }
        
        .chat-name {
            font-weight: 600;
            margin-bottom: 4px;
        }
        
        .chat-preview {
            font-size: 0.85rem;
            color: #777;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .chat-time {
            font-size: 0.75rem;
            color: #999;
        }
        
        .main-content {
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
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .chat-header-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(135deg, #a5b4fc, #818cf8);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.2rem;
        }
        
        .chat-header-info h3 {
            font-weight: 600;
            margin-bottom: 4px;
        }
        
        .chat-header-info p {
            font-size: 0.9rem;
            color: #4ade80;
        }
        
        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 20px;
            background: #f8fafc;
        }
        
        .message {
            max-width: 70%;
            padding: 15px;
            border-radius: 18px;
            position: relative;
            line-height: 1.5;
        }
        
        .message.received {
            align-self: flex-start;
            background: white;
            border-top-left-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
        }
        
        .message.sent {
            align-self: flex-end;
            background: linear-gradient(135deg, #ff4d6d, #ff8fa3);
            color: white;
            border-top-right-radius: 5px;
        }
        
        .message-time {
            font-size: 0.7rem;
            margin-top: 5px;
            text-align: right;
            opacity: 0.7;
        }
        
        .image-message {
            border-radius: 15px;
            overflow: hidden;
            margin-top: 10px;
        }
        
        .image-message img {
            width: 100%;
            display: block;
        }
        
        .chat-input {
            padding: 20px;
            border-top: 1px solid #eee;
            display: flex;
            gap: 10px;
            background: white;
        }
        
        .chat-input input {
            flex: 1;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 25px;
            outline: none;
            font-size: 1rem;
        }
        
        .chat-input input:focus {
            border-color: #ff8fa3;
        }
        
        .chat-input button {
            background: linear-gradient(135deg, #ff4d6d, #ff8fa3);
            color: white;
            border: none;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .chat-input button:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 10px rgba(255, 77, 109, 0.3);
        }
        
        .upload-section {
            width: 300px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            padding: 20px;
            display: flex;
            flex-direction: column;
        }
        
        .upload-section h2 {
            color: #ff4d6d;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }
        
        .upload-area {
            border: 2px dashed #ff8fa3;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .upload-area:hover {
            background: #fff5f7;
        }
        
        .upload-area i {
            font-size: 3rem;
            color: #ff4d6d;
            margin-bottom: 15px;
        }
        
        .upload-btn {
            background: linear-gradient(135deg, #ff4d6d, #ff8fa3);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .upload-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.3);
        }
        
        .recent-images {
            margin-top: 20px;
        }
        
        .image-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-top: 10px;
        }
        
        .image-item {
            aspect-ratio: 1;
            border-radius: 10px;
            overflow: hidden;
            cursor: pointer;
        }
        
        .image-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s ease;
        }
        
        .image-item:hover img {
            transform: scale(1.05);
        }
        
        footer {
            text-align: center;
            padding: 20px;
            color: #777;
            font-size: 0.9rem;
            background: white;
            margin-top: auto;
            border-top: 1px solid #eee;
        }
        
        @media (max-width: 1100px) {
            .container {
                flex-direction: column;
            }
            
            .sidebar, .upload-section {
                width: 100%;
            }
            
            .image-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }
        
        @media (max-width: 768px) {
            .message {
                max-width: 85%;
            }
            
            .image-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }
        
        @media (max-width: 480px) {
            header {
                padding: 1rem;
            }
            
            .logo h1 {
                font-size: 1.4rem;
            }
            
            .container {
                padding: 10px;
            }
            
            .image-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">
            <i class="fas fa-heart"></i>
            <h1>My Chat Picture</h1>
        </div>
        <div class="user-info">
            <div class="user-avatar">आप</div>
            <span>आपका नाम</span>
        </div>
    </header>
    
    <div class="container">
        <div class="sidebar">
            <h2>हाल की चैट</h2>
            <div class="chat-list">
                <div class="chat-item active">
                    <div class="chat-avatar">पू</div>
                    <div class="chat-info">
                        <div class="chat-name">पूजा</div>
                        <div class="chat-preview">यह तस्वीर देखो, कितनी सुंदर है!</div>
                    </div>
                    <div class="chat-time">10:24</div>
                </div>
                <div class="chat-item">
                    <div class="chat-avatar">रा</div>
                    <div class="chat-info">
                        <div class="chat-name">राहुल</div>
                        <div class="chat-preview">कल वाली फोटो भेज सकते हो?</div>
                    </div>
                    <div class="chat-time">09:45</div>
                </div>
                <div class="chat-item">
                    <div class="chat-avatar">प्र</div>
                    <div class="chat-info">
                        <div class="chat-name">प्रिया</div>
                        <div class="chat-preview">नई प्रोफाइल पिक बहुत अच्छी है!</div>
                    </div>
                    <div class="chat-time">कल</div>
                </div>
                <div class="chat-item">
                    <div class="chat-avatar">अ</div>
                    <div class="chat-info">
                        <div class="chat-name">अमित</div>
                        <div class="chat-preview">आपके साथ एक फोटो शेयर की</div>
                    </div>
                    <div class="chat-time">कल</div>
                </div>
                <div class="chat-item">
                    <div class="chat-avatar">स</div>
                    <div class="chat-info">
                        <div class="chat-name">सोनम</div>
                        <div class="chat-preview">फोटो के लिए धन्यवाद!</div>
                    </div>
                    <div class="chat-time">सोमवार</div>
                </div>
            </div>
        </div>
        
        <div class="main-content">
            <div class="chat-header">
                <div class="chat-header-avatar">पू</div>
                <div class="chat-header-info">
                    <h3>पूजा</h3>
                    <p>ऑनलाइन</p>
                </div>
            </div>
            
            <div class="chat-messages">
                <div class="message received">
                    <p>अरे! यह हार्ट इमेज देखो जो मुझे मिली!</p>
                    <div class="image-message">
                        <img src="https://images.unsplash.com/photo-1570196917327-9d9d6c4213be?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=600&q=80" alt="Heart image">
                    </div>
                    <div class="message-time">10:15 AM</div>
                </div>
                
                <div class="message sent">
                    <p>वाह, यह तो बहुत सुंदर है! रंग कितने अद्भुत हैं।</p>
                    <div class="message-time">10:18 AM</div>
                </div>
                
                <div class="message received">
                    <p>हां ना? यह हमारे लोगो की याद दिलाती है। यह एक और देखो:</p>
                    <div class="image-message">
                        <img src="https://images.unsplash.com/photo-1518568814500-bf0f8d125f46?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=600&q=80" alt="Red heart">
                    </div>
                    <div class="message-time">10:22 AM</div>
                </div>
                
                <div class="message sent">
                    <p>यह तो बहुत अच्छी वॉलपेपर बनेंगी! क्या आप हाई-रिज़ॉल्यूशन वर्जन भेज सकती हो?</p>
                    <div class="message-time">10:24 AM</div>
                </div>
            </div>
            
            <div class="chat-input">
                <input type="text" placeholder="मैसेज टाइप करें...">
                <button><i class="fas fa-paper-plane"></i></button>
            </div>
        </div>
        
        <div class="upload-section">
            <h2>तस्वीरें शेयर करें</h2>
            <div class="upload-area">
                <i class="fas fa-cloud-upload-alt"></i>
                <p>तस्वीरें यहाँ ड्रैग करें या ब्राउज़ करने के लिए क्लिक करें</p>
            </div>
            <button class="upload-btn">
                <i class="fas fa-upload"></i>
                तस्वीर अपलोड करें
            </button>
            
            <div class="recent-images">
                <h3>हाल की तस्वीरें</h3>
                <div class="image-grid">
                    <div class="image-item">
                        <img src="https://images.unsplash.com/photo-1542037104857-ffbb0b9155fb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80" alt="Image 1">
                    </div>
                    <div class="image-item">
                        <img src="https://images.unsplash.com/photo-1570196917327-9d9d6c4213be?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80" alt="Image 2">
                    </div>
                    <div class="image-item">
                        <img src="https://images.unsplash.com/photo-1518568814500-bf0f8d125f46?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80" alt="Image 3">
                    </div>
                    <div class="image-item">
                        <img src="https://images.unsplash.com/photo-1584820927498-cfe5211fd8bf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=300&q=80" alt="Image 4">
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <p>My Chat Picture &copy; 2023 - अपने पलों को अपनों के साथ शेयर करें</p>
    </footer>

    <script>
        // Simple JavaScript for interactive elements
        document.addEventListener('DOMContentLoaded', function() {
            // Chat item selection
            const chatItems = document.querySelectorAll('.chat-item');
            chatItems.forEach(item => {
                item.addEventListener('click', function() {
                    chatItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Update chat header with selected contact
                    const contactName = this.querySelector('.chat-name').textContent;
                    const contactAvatar = this.querySelector('.chat-avatar').textContent;
                    document.querySelector('.chat-header-avatar').textContent = contactAvatar;
                    document.querySelector('.chat-header-info h3').textContent = contactName;
                });
            });
            
            // Send message functionality
            const chatInput = document.querySelector('.chat-input input');
            const sendButton = document.querySelector('.chat-input button');
            
            function sendMessage() {
                const messageText = chatInput.value.trim();
                if (messageText) {
                    const messagesContainer = document.querySelector('.chat-messages');
                    
                    const newMessage = document.createElement('div');
                    newMessage.className = 'message sent';
                    newMessage.innerHTML = `
                        <p>${messageText}</p>
                        <div class="message-time">${new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</div>
                    `;
                    
                    messagesContainer.appendChild(newMessage);
                    chatInput.value = '';
                    
                    // Scroll to bottom
                    messagesContainer.scrollTop = messagesContainer.scrollHeight;
                    
                    // Simulate reply after a short delay
                    setTimeout(() => {
                        const replies = [
                            "यह तो दिलचस्प है!",
                            "मैं इसे चेक करूंगा।",
                            "शेयर करने के लिए धन्यवाद!",
                            "क्या आप और जानकारी भेज सकते हैं?",
                            "मुझे यह बहुत पसंद आया!"
                        ];
                        
                        const randomReply = replies[Math.floor(Math.random() * replies.length)];
                        
                        const replyMessage = document.createElement('div');
                        replyMessage.className = 'message received';
                        replyMessage.innerHTML = `
                            <p>${randomReply}</p>
                            <div class="message-time">${new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</div>
                        `;
                        
                        messagesContainer.appendChild(replyMessage);
                        messagesContainer.scrollTop = messagesContainer.scrollHeight;
                    }, 1000);
                }
            }
            
            sendButton.addEventListener('click', sendMessage);
            
            chatInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            // Upload area interaction
            const uploadArea = document.querySelector('.upload-area');
            const uploadBtn = document.querySelector('.upload-btn');
            
            uploadArea.addEventListener('click', function() {
                alert('यहाँ अपलोड फंक्शन इम्प्लीमेंट किया जाएगा!');
            });
            
            uploadBtn.addEventListener('click', function() {
                alert('यहाँ अपलोड फंक्शन इम्प्लीमेंट किया जाएगा!');
            });
        });
    </script>
</body>
</html>
