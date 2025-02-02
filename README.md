<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reverse Alphabet Translator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
        }
        button {
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Reverse Alphabet Translator</h1>
    <p>Type a word and click "Translate" to see it in reverse alphabet:</p>

    <input type="text" id="inputText" placeholder="Enter text here">
    <button onclick="translateToReverseAlphabet()">Translate</button>

    <div id="result"></div>
    <button id="copyButton" style="display: none;" onclick="copyToClipboard()">Copy to Clipboard</button>

    <script>
        function translateToReverseAlphabet() {
            const inputText = document.getElementById('inputText').value;
            let result = '';

            // Reverse alphabet mapping
            const alphabet = 'abcdefghijklmnopqrstuvwxyz';
            const reversedAlphabet = 'zyxwvutsrqponmlkjihgfedcba';

            // Iterate over each character in the input and translate it
            for (let i = 0; i < inputText.length; i++) {
                const char = inputText[i].toLowerCase();
                if (alphabet.includes(char)) {
                    const index = alphabet.indexOf(char);
                    result += inputText[i] === inputText[i].toUpperCase() ? 
                            reversedAlphabet[index].toUpperCase() : 
                            reversedAlphabet[index];
                } else {
                    result += inputText[i]; // non-alphabetic characters remain unchanged
                }
            }

            // Display the result and show the copy button
            document.getElementById('result').innerText = "Translated: " + result;
            document.getElementById('copyButton').style.display = 'inline-block';
        }

        function copyToClipboard() {
            const resultText = document.getElementById('result').innerText.replace("Translated: ", "");
            const textArea = document.createElement('textarea');
            textArea.value = resultText;
            document.body.appendChild(textArea);
            textArea.select();
            document.execCommand('copy');
            document.body.removeChild(textArea);
            alert("Copied to clipboard!");
        }
    </script>
</body>
</html>
