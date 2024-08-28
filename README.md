- 👋 Hi, I’m @Tatelles
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Tatelles/Tatelles is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->


!DOCTYPE html>

<html lang="pt-BR">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Criptografia de Texto</title>

    <link rel="stylesheet" href="styles.css">

</head>

<body>

    <div class="container">

        <h1>Criptografia de Texto</h1>

        <textarea id="inputText" placeholder="Digite o texto aqui..."></textarea>

        <div class="controls">

            <button id="encryptBtn">Criptografar</button>

            <button id="decryptBtn">Descriptografar</button>

            <button id="copyBtn">Copiar</button>

        </div>

        <textarea id="outputText" placeholder="Resultado aparecerá aqui..."></textarea>

    </div>

    <script src="script.js"></script>

</body>

</html>


body {

    font-family: Arial, sans-serif;

    display: flex;

    justify-content: center;

    align-items: center;

    height: 100vh;

    margin: 0;

    background-color: #f0f0f0;

}


.container {

    text-align: center;

    width: 80%;

    max-width: 800px;

}


textarea {

    width: 100%;

    height: 100px;

    margin: 10px 0;

    padding: 10px;

    font-size: 16px;

    border: 1px solid #ccc;

    border-radius: 4px;

}


button {

    margin: 5px;

    padding: 10px 20px;

    font-size: 16px;

    cursor: pointer;

}

const encryptionRules = {

    'e': 'enter',

    'i': 'imes',

    'a': 'ai',

    'o': 'ober',

    'u': 'ufat'

};


const decryptionRules = Object.fromEntries(

    Object.entries(encryptionRules).map(([key, value]) => [value, key])

);


function encrypt(text) {

    return text.split('').map(char => encryptionRules[char] || char).join('');

}


function decrypt(text) {

    for (const [key, value] of Object.entries(decryptionRules)) {

        text = text.split(key).join(value);

    }

    return text;

}


document.getElementById('encryptBtn').addEventListener('click', () => {

    const inputText = document.getElementById('inputText').value;

    document.getElementById('outputText').value = encrypt(inputText);

});


document.getElementById('decryptBtn').addEventListener('click', () => {

    const inputText = document.getElementById('inputText').value;

    document.getElementById('outputText').value = decrypt(inputText);

});


document.getElementById('copyBtn').addEventListener('click', () => {

    const outputText = document.getElementById('outputText');

    outputText.select();

    document.execCommand('copy');

});




