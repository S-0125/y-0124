
![微信图片_20251022102100_58_41(1)(1)](https://github.com/user-attachments/assets/e88d8ee3-33ac-44af-b242-ae8231d4df3a)
(https://github.com/user-attachments/files/23760471/default.html)

<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>生日快乐</title>
    <style>
        
        body {
            margin: 0;
            padding: 50px 0;
            background-color: #f0f8ff;
            font-family: KaiTi, "楷体", serif;
            text-align: center;
        }

        
        h1 {
            color: #e91e63;
            font-size: 28px;
            margin-bottom: 40px;
        }

        
        .btn {
            background-color: #e91e63;
            color: white;
            border: none;
            border-radius: 30px;
            font-size: 18px;
            font-family: KaiTi, "楷体", serif;
            padding: 12px 30px;
            margin: 0 15px;
            cursor: pointer;
            transition: transform 0.3s, opacity 0.3s;
        }

       
        .btn:hover {
            transform: scale(1.05);
            opacity: 0.9;
        }

        
        .blessing-popup {
            position: fixed;
            width: 220px;
            height: 100px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 16px;
           
            animation: popIn 0.5s ease forwards;
            transform-origin: center;
        }

        
        @keyframes popIn {
            0% {
                transform: scale(0);
            }
            100% {
                transform: scale(1);
            }
        }

       
        .btn:disabled {
            background-color: #ccc;
            cursor: not-allowed;
            transform: none;
            opacity: 1;
        }
    </style>
</head>
<body>
    
    <h1>点击开始接收祝福吧！</h1>
    
    <button class="btn" id="openBtn">开启祝福</button>
    <button class="btn" id="closeBtn">关闭所有</button>

    <script>
        
        const openBtn = document.getElementById('openBtn');
        const closeBtn = document.getElementById('closeBtn');
       
        const bgColors = [
            '#ffc0cb', '#ffb6c1', '#ff69b4', '#ff1493', '#db7093',
            '#bc8f8f', '#c71585', '#ffa07a', '#ff7f50', '#ffa500',
            '#ffffe0', '#e6e6fa', '#d8bfd8', '#dda0dd', '#ee82ee'
        ];
        
        let popups = [];

       
        function createPopup() {
           
            const popup = document.createElement('div');
            popup.className = 'blessing-popup';
            
            
            const randomColor = bgColors[Math.floor(Math.random() * bgColors.length)];
            popup.style.backgroundColor = randomColor;
            
           
            const maxTop = window.innerHeight - 100; 
            const maxLeft = window.innerWidth - 220; 
            popup.style.top = `${Math.floor(Math.random() * maxTop)}px`;
            popup.style.left = `${Math.floor(Math.random() * maxLeft)}px`;
            
           
            const blessings = [
                '苏宝，愿你平安喜乐！', '祝宝宝事事顺遂～', '宝宝，每天都要开心呀！',
                '愿宝宝前程似锦！', '宝宝，好运常伴你左右！', '祝宝宝健康无忧～'
            ];
            popup.textContent = blessings[Math.floor(Math.random() * blessings.length)];
            
           
            document.body.appendChild(popup);
            popups.push(popup);
        }

        
        openBtn.addEventListener('click', function() {
           
            openBtn.disabled = true;
            
            
            let count = 0;
            const popupInterval = setInterval(() => {
                createPopup();
                count++;
               
                if (count >= 100) {
                    clearInterval(popupInterval);
                }
            }, 50);
            
            
            setTimeout(() => {
                openBtn.disabled = false;
            }, 5000);
        });

       
        closeBtn.addEventListener('click', function() {
            
            popups.forEach(popup => {
                document.body.removeChild(popup);
            });
           
            popups = [];
        });
    </script>
</body>
</html>
