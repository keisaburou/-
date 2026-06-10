<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>お化け屋敷 - QR スキャナー</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            text-align: center;
            background-color: #1a1a1a;
            color: white;
            font-family: Arial, sans-serif;
        }
        button {
            padding: 15px 30px;
            font-size: 18px;
            background-color: #ff3333;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 10px;
        }
        button:hover {
            background-color: #cc0000;
        }
        #screen {
            width: 100%;
            height: 100vh;
            position: fixed;
            top: 0;
            left: 0;
            background-color: rgba(0, 0, 0, 0);
            display: none;
            z-index: 1000;
        }
        #screen.active {
            display: block;
            background-color: rgba(0, 0, 0, 0.9);
        }
    </style>
</head>
<body>
    <h1>👻 お化け屋敷へようこそ 👻</h1>
    <p>下のボタンを押して、恐怖を体験してください...</p>
    
    <button onclick="startScream()">驚く準備はいい？</button>
    
    <div id="screen"></div>
    <audio id="screamSound" src="https://example.com/scream.mp3"></audio>

    <script>
        function startScream() {
            // 暗転
            document.getElementById('screen').classList.add('active');
            
            // 音声再生
            const audio = document.getElementById('screamSound');
            audio.play().catch(e => console.log('音声再生エラー:', e));
            
            // 振動
            if (navigator.vibrate) {
                navigator.vibrate([200, 100, 200, 100, 500]); // ビビビ...っという振動パターン
            }
            
            // 3秒後に暗転を解除
            setTimeout(() => {
                document.getElementById('screen').classList.remove('active');
            }, 3000);
        }
    </script>
</body>
</html>