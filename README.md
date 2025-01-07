<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!DOCTYPE html>
    <html lang="ru">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Магический шар предсказаний</title>
        <style>
            body {
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                min-height: 100vh;
                margin: 0;
                background-color: #1a1a1a;
                color: white;
                font-family: Arial, sans-serif;
            }
    
            .magic-ball {
                width: 200px;
                height: 200px;
                background: radial-gradient(circle at 70px 70px, #333, #000);
                border-radius: 50%;
                margin: 20px;
                cursor: pointer;
                transition: transform 0.3s;
            }
    
            .magic-ball:hover {
                transform: scale(1.1);
            }
    
            #question {
                padding: 10px;
                margin: 20px;
                width: 300px;
                border-radius: 5px;
            }
    
            #answer {
                margin: 20px;
                font-size: 18px;
                text-align: center;
            }
    
            button {
                padding: 10px 20px;
                background-color: #4CAF50;
                color: white;
                border: none;
                border-radius: 5px;
                cursor: pointer;
            }
    
            button:hover {
                background-color: #45a049;
            }
        </style>
    </head>
    <body>
        <h1>Магический шар предсказаний</h1>
        <input type="text" id="question" placeholder="Задайте свой вопрос...">
        <div class="magic-ball" onclick="getPrediction()"></div>
        <div id="answer"></div>
    
        <script>
            async function getPrediction() {
                const question = document.getElementById('question').value;
                if (!question) {
                    alert('Пожалуйста, задайте вопрос!');
                    return;
                }
    
                try {
                    const response = await fetch('https://eightballapi.com/api', {
                        method: 'GET'
                    });
                    const data = await response.json();
                    document.getElementById('answer').textContent = data.reading;
                } catch (error) {
                    console.error('Ошибка:', error);
                    document.getElementById('answer').textContent = 'Произошла ошибка при получении предсказания';
                }
            }
        </script>

// ... existing code ...

<script>
    const predictions = [
        "Да, определенно",
        "Можешь быть уверен в этом",
        "Без сомнения",
        "Определённо да",
        "Можешь положиться на это",
        "Как я вижу, да",
        "Вероятнее всего",
        "Хорошие перспективы",
        "Знаки говорят — да",
        "Да",
        "Пока не ясно, попробуй снова",
        "Спроси позже",
        "Лучше не рассказывать",
        "Сейчас нельзя предсказать",
        "Сконцентрируйся и спроси опять",
        "Даже не думай",
        "Мой ответ — нет",
        "По моим данным — нет",
        "Перспективы не очень хорошие",
        "Весьма сомнительно"
    ];

    async function getPrediction() {
        const question = document.getElementById('question').value;
        if (!question) {
            alert('Пожалуйста, задайте вопрос!');
            return;
        }

        try {
            // Добавляем анимацию встряхивания шара
            const magicBall = document.querySelector('.magic-ball');
            magicBall.style.animation = 'shake 0.5s';
            
            // Получаем случайное предсказание
            const randomIndex = Math.floor(Math.random() * predictions.length);
            const prediction = predictions[randomIndex];
            
            // Небольшая задержка для эффекта
            setTimeout(() => {
                document.getElementById('answer').textContent = prediction;
                magicBall.style.animation = '';
            }, 500);
        } catch (error) {
            console.error('Ошибка:', error);
            document.getElementById('answer').textContent = 'Произошла ошибка при получении предсказания';
        }
    }
</script>

<style>
    /* Добавляем в существующие стили анимацию встряхивания */
    @keyframes shake {
        0% { transform: translate(1px, 1px) rotate(0deg); }
        10% { transform: translate(-1px, -2px) rotate(-1deg); }
        20% { transform: translate(-3px, 0px) rotate(1deg); }
        30% { transform: translate(3px, 2px) rotate(0deg); }
        40% { transform: translate(1px, -1px) rotate(1deg); }
        50% { transform: translate(-1px, 2px) rotate(-1deg); }
        60% { transform: translate(-3px, 1px) rotate(0deg); }
        70% { transform: translate(3px, 1px) rotate(-1deg); }
        80% { transform: translate(-1px, -1px) rotate(1deg); }
        90% { transform: translate(1px, 2px) rotate(0deg); }
        100% { transform: translate(1px, -2px) rotate(-1deg); }
    }
</style>

// ... existing code ...
    </body>
    </html>
</body>
</html>
