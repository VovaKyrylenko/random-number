Я знаю, що ти читаєш це, бо шукаєш найабсурдніший код, пупупу, я тут! дивіться що я тут наклацав! 😅

Якщо не хочеться багато читати:

[ЗАПУСК](#run-it)

[нормальний запуск](#run-it-normally)

Коротше, сидів я такий з ранку, попиваю каву, думаю - треба зробити рандомне число. Ну і знаєте, як то буває - замість нормального Math.random() мене понесло в такі дебрі... 🤪

Дивіться на цю красу:
```javascript
console.log(Math.floor(Number(String(Number(String(new Date().getSeconds())) * Number(String(42)) % Number(String(100))) + Number(String(1))) * Number(String((Number(String(Math.PI * 100)).toFixed(2))) % Number(String(new Date().getMilliseconds() % 50 + 1))) / Number(String(Number(String(Math.abs(-100))) + Number(String(new Date().getDay()))) % 100) + Number(String(100 / 2)) - Number(String(50)) + Number(String((new Date().getHours() + "").charAt(1) || 1)) * Number(String(new Date().getMinutes() % 10)) % Number(String(7) + Math.PI)));
```

Давайте візьмемо секунди, помножимо на 42 (ну бо класика, всі ж "Автостопом по галактиці" читали), потім закинемо туди π (бо я на фізматі вчився, без π життя не життя 😂).
А потім як пішло-поїхало! Години, хвилини, мілісекунди - все в кашу! Перетворюємо в рядки, назад в числа, знову в рядки... Прямо як мій мозок в п'ятницю ввечері після деплою! 

Знаєте, чим цей код нагадує моє життя? 
- Зовні виглядає складно ✅
- Всередині повний безлад ✅
- Але якимось дивом працює ✅

Найсмішніше, що цей монстр просто видає рандомне число. Це як піти в магазин за хлібом через сусіднє місто!
Цей монстр Франкенштейна насправді можна було написати просто як:

```javascript
const randomNumber = Math.floor(Math.random() * 100);
```

Але ж де тоді веселощі? Де драма? Де можливість похизуватися перед колегами цим шедевром? 😎
До речі, коли показав цей код колезі, він довго дивився на монітор, потім на мене, потім знову на монітор і сказав: "Чувак, ти точно спиш?" 😅
Коротше, це мій маленький пам'ятник тому, як не треба писати код. Але погодьтеся, виглядає епічно! 😎

P.S. Якщо хтось захоче використати цей код - я вас попередив! Потім не кажіть, що не знали, на що підписувалися 🤣

P.P.S. А ви знали, що якщо цей код запустити рівно о 3:14:15, то він видасть... абсолютно випадкове число, як і в будь-який інший час? Магія математики! ✨
Дякую за увагу! Піду писати дисертацію на тему "Вплив дня тижня на генерацію псевдовипадкових чисел у контексті сучасного веб-програмування". Керівник сказав, що це проривне дослідження! 🎓🤪


# RUN IT

1️⃣ Спочатку створюємо Docker контейнер для нашого ГЕНІАЛЬНОГО коду:

```dockerfile
FROM node:latest
WORKDIR /usr/src/app
RUN echo "console.log(Math.floor(Number(String(Number(String(new Date().getSeconds())) * Number(String(42)) % Number(String(100))) + Number(String(1))) * Number(String((Number(String(Math.PI * 100)).toFixed(2))) % Number(String(new Date().getMilliseconds() % 50 + 1))) / Number(String(Number(String(Math.abs(-100))) + Number(String(new Date().getDay()))) % 100) + Number(String(100 / 2)) - Number(String(50)) + Number(String((new Date().getHours() + "").charAt(1) || 1)) * Number(String(new Date().getMinutes() % 10)) % Number(String(7) + Math.PI)));" > random.js
CMD ["node", "random.js"]
```

2️⃣ Тепер створюємо bash-скрипт, який запускає це все через Python (бо чому б і ні? 😅):

```bash
#!/bin/bash

echo '
import os
import time
print("🚀 Підготовка до запуску найкращого генератора випадкових чисел...")
time.sleep(2)
print("⚡ Розігріваємо процесор...")
time.sleep(1)
print("🔥 Калібруємо квантові флуктуації...")
time.sleep(1)
print("🌟 Синхронізуємо з зірками...")
time.sleep(1)
print("\n🎯 Запускаємо Docker контейнер з нашим мега-кодом:\n")
os.system("docker build -t random-number-generator . && docker run --rm random-number-generator")
' > run_random.py

# Даємо файлу права на виконання
chmod +x run_random.py

# Запускаємо через Python, бо чому б і ні?
python3 run_random.py
```

3️⃣ А тепер фінальний удар - запускаємо це все через AWS Lambda! 😈

```javascript
const AWS = require('aws-sdk');
const lambda = new AWS.Lambda();

const params = {
  FunctionName: 'random-number-generator',
  Runtime: 'nodejs18.x',
  Handler: 'index.handler',
  Role: 'arn:aws:iam::YOUR_ACCOUNT:role/lambda-role',
  Code: {
    ZipFile: Buffer.from(`
      exports.handler = async (event) => {
        const randomNumber = Math.floor(Number(String(Number(String(new Date().getSeconds())) * Number(String(42)) % Number(String(100))) + Number(String(1))) * Number(String((Number(String(Math.PI * 100)).toFixed(2))) % Number(String(new Date().getMilliseconds() % 50 + 1))) / Number(String(Number(String(Math.abs(-100))) + Number(String(new Date().getDay()))) % 100) + Number(String(100 / 2)) - Number(String(50)) + Number(String((new Date().getHours() + "").charAt(1) || 1)) * Number(String(new Date().getMinutes() % 10)) % Number(String(7) + Math.PI));
        
        return {
          statusCode: 200,
          body: JSON.stringify({
            message: '🎲 НАЙЕПІЧНІШЕ РАНДОМНЕ ЧИСЛО З AWS:',
            number: randomNumber
          })
        };
      };
    `)
  }
};
```

4️⃣ І все це запакувати в npm-пакет з назвою `over-engineered-random-number` 🤣

```json
{
  "name": "over-engineered-random-number",
  "version": "1.0.0",
  "description": "Найскладніший спосіб отримати випадкове число в історії JavaScript",
  "scripts": {
    "start": "echo 'Починаємо магію...' && python3 run_random.py",
    "start:docker": "docker-compose up",
    "start:aws": "node deploy-to-aws.js",
    "start:all": "npm run start && npm run start:docker && npm run start:aws",
    "why": "echo 'Тому що можемо! 😎'"
  }
}
```

5️⃣ І запускати це все одним рядком:

```bash
npx create-react-app random-app && cd random-app && npm i over-engineered-random-number && npm run start:all
```

P.S. Якщо ваш тімлід побачить це в продакшені, просто скажіть що це "мікросервісна архітектура для оптимізації генерації випадкових чисел з використанням хмарних технологій" 🤣
P.P.S. Цей спосіб настільки абсурдний, що навіть Docker контейнер намагається втекти з комп'ютера! 🏃‍♂️


# Run it normally

Запустити цей код можна досить просто, і ось кілька способів, як це зробити:

1. У консолі браузера
  
  1.	Відкрийте браузер (Google Chrome, Firefox, Safari або інший).
	2.	Натисніть праву кнопку миші на сторінці та виберіть “Перевірити” (або “Inspect”).
	3.	Перейдіть на вкладку “Консоль” (Console).
	4.	Вставте ваш код у консоль і натисніть Enter.

2. У Node.js

Якщо у вас встановлено Node.js, ви можете запустити код так:

  1.	Створіть новий файл з розширенням .js, наприклад, randomNumber.js.
	2.	Скопіюйте ваш код і вставте його у файл.
	3.	Відкрийте термінал (командний рядок).
	4.	Перейдіть до папки, де знаходиться ваш файл, за допомогою команди cd.
	5.	Запустіть файл за допомогою команди:

```bash
node randomNumber.js
```

3. В онлайн-редакторі

Можна також скористатися онлайн-редакторами, такими як:

  •	JSFiddle
	•	CodePen
	•	Replit

Просто вставте ваш код у відповідне поле для JavaScript і натисніть “Запустити”.
