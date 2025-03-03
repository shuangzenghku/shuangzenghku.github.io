<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>登录示例</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f2f2f2;
            position: relative; /* 允许绝对定位 */
        }
        #login-container {
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            width: 300px;
        }
        #content {
            display: none;
            text-align: center;
        }
        img {
            max-width: 100%;
            height: auto;
            margin-top: 10px;
        }
        #music-player {
            position: absolute;
            top: 20px;
            right: 20px;
            background: white;
            padding: 15px; /* 增加内边距 */
            border-radius: 5px;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
            z-index: 10; /* 确保播放器在最上层 */
            width: 250px; /* 增加播放器的宽度 */
        }
        audio {
            width: 100%; /* 设置音频播放器宽度为 100% */
        }
        #gallery {
            margin-top: 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }
        .gallery-image {
            margin: 5px;
            width: 100px; /* 设置相册图片的宽度 */
            height: 100px; /* 设置相册图片的高度 */
            overflow: hidden;
            border-radius: 5px;
            cursor: pointer; /* 鼠标悬停时显示为手形 */
            display: flex; /* 使用 Flexbox 对齐内容 */
            justify-content: center; /* 水平居中 */
            align-items: center; /* 垂直居中 */
        }
        .gallery-image img {
            width: 100%;
            height: 100%; /* 使图片填满容器 */
            object-fit: cover; /* 保持图片比例并填满容器 */
        }
        /* 模态框样式 */
        #modal {
            display: none; /* 默认隐藏 */
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
        }
        #modal img {
            max-width: 90%;
            max-height: 90%;
        }
        .close {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            font-size: 30px;
            font-weight: bold;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div id="login-container">
    <h2>login</h2>
    <input type="text" id="username" placeholder="name" required>
    <input type="password" id="password" placeholder="password" required>
    <button onclick="login()">login</button>
    <p id="error-message" style="color: red;"></p>
</div>

<div id="content">
    <h1>Hello, This is Takuya!</h1>
    <img src="butterbear.jpg">

    <div id="music-player">
        <h3>PlayMe</h3>
        <audio id="audio-player" controls loop>
            <source id="audio-source" src="https://path-to-your-music/song1.mp3" type="audio/mpeg">
        </audio>
        <select id="song-selector" onchange="changeSong()">
            <option value="" disabled selected>My favorite songs</option>
            <option value="美好的日子.mp3">Beautiful Day</option>
            <option value="枫.mp3">Maple</option>
            <option value="龙猫.mp3">Totoro</option>
            <option value="温柔.mp3">Tenderness</option>
            <option value="听见下雨的声音.mp3">Rhythm of the Rain</option>
        </select>
    </div>

    <div id="gallery">
        <div class="gallery-image" onclick="openModal('image1.jpg')"><img src="image1.jpg"></div>
        <div class="gallery-image" onclick="openModal('image2.jpg')"><img src="image2.jpg"></div>
        <div class="gallery-image" onclick="openModal('image3.jpg')"><img src="image3.jpg"></div>
        <div class="gallery-image" onclick="openModal('image4.jpg')"><img src="image4.jpg"></div>
    </div>
</div>

<!-- 模态框 -->
<div id="modal" onclick="closeModal()">
    <span class="close" onclick="closeModal()">&times;</span>
    <img id="modal-image" src="" alt="大图">
</div>

<script>
    function login() {
        const username = document.getElementById('username').value;
        const password = document.getElementById('password').value;
        const errorMessage = document.getElementById('error-message');

        // 替换为你自己的用户名和密码
        if (username === 'takuya' && password === 'takuya') {
            document.getElementById('login-container').style.display = 'none';
            document.getElementById('content').style.display = 'block';
        } else {
            errorMessage.textContent = 'You are not a friend of Takuya!';
        }
    }

    function changeSong() {
        const songSelector = document.getElementById('song-selector');
        const audioPlayer = document.getElementById('audio-player');
        const audioSource = document.getElementById('audio-source');
        
        audioSource.src = songSelector.value;
        audioPlayer.load();
        audioPlayer.play();
    }

    function openModal(imageSrc) {
        const modal = document.getElementById('modal');
        const modalImage = document.getElementById('modal-image');
        modalImage.src = imageSrc;
        modal.style.display = 'flex'; // 显示模态框
    }

    function closeModal() {
        const modal = document.getElementById('modal');
        modal.style.display = 'none'; // 隐藏模态框
    }
</script>

</body>
</html>
