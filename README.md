# ChatGPT Translator
:star: Translate your text using **ChatGPT**!

This translator uses ChatGPT to translate your text. ChatGPT can understand slang in all languages.
This API uses official OpenAI API. You need to create own API key to use it.

# Example of usage
I made a few examples in different programming languages.

Python:
```python
import chatgpt_translator as Translator # Copy 'chatgpt_translator.py' from this repository inside your project

print(Translator.Translate(source_text = "Hello, how are you?", awaited_lang = "Russian", token = "sk-...")["translated_text"]) # Привет, как дела?
```

Other programming languages:

To translate text in other languages, you need to send **GET** request to [server hosted on replit](https://chatgpttranslator.netrumnetrum.repl.co/translate)

There 3 required parameters:
- ``text`` - Raw text
- ``awaited_lang`` - Language for translation, for example: English, or Russian
- ``token`` - OpenAI API token

If everything is ok, you will get same response:

```json
{
        "source_text": "Hello, how are you?",
        "translated_text": "Привет, как дела?",
        "awaited_lang": "ru"
}
```

Here example in Java:

```java
import org.json.JSONObject;

import java.io.*;
import java.net.URL;
import java.net.URLConnection;
import java.nio.charset.StandardCharsets;

public static void main(String[] args) throws IOException {
        String api = "https://chatgpttranslator.netrumnetrum.repl.co/translate";
        URLConnection connection = new URL(String.format("%s?text=%s&awaited_lang=%s&token=%s",
                api, // API Host
                "Hello, how are you?".replace(" ", "%20"), // Input text
                "Russian", // Awaited language
                "sk-..." // OpenAI token
        )).openConnection();


        // Read the response
        String response = new BufferedReader(new InputStreamReader(connection.getInputStream(), StandardCharsets.UTF_8)).readLine();

        JSONObject json = new JSONObject(response);
        String rawText = json.getString("translated_text"); // This API returns JSON-style response. We need to parse it.

        System.out.printf("%s\n", rawText); // Привет, как дела?
    }
```
