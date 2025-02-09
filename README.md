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
        <div>
            <button onclick="changeSong('美好的日子.mp3')">Beautiful Day</button>
            <button onclick="changeSong('枫.mp3')">Maple</button>
            <button onclick="changeSong('龙猫.mp3')">Totoro</button>
        </div>
    </div>
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

    function changeSong(songUrl) {
        const audioPlayer = document.getElementById('audio-player');
        const audioSource = document.getElementById('audio-source');
        audioSource.src = songUrl;
        audioPlayer.load();
        audioPlayer.play();
    }
</script>

</body>
</html>
