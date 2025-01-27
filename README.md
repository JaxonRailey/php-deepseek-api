# DeepSeek PHP Class

The `DeepSeek` class is a PHP wrapper designed to interact with DeepSeek's API, specifically for chat completions. Below is a guide on how to use this class effectively.

## Installation

Ensure you have PHP installed with cURL support. You can include the `DeepSeek` class in your project by requiring the file containing the class.

```php
require_once 'path/to/DeepSeek.php';
```

## Initialization

Create an instance of the `DeepSeek` class.

```php
$deepseek = new DeepSeek();
```

## Setting the API Key

You need to set your DeepSeek API key to authenticate requests.

```php
$deepseek->key('your-api-key-here');
```

## Using the Chat

### Setting the Model

You can specify the model to use for chat completions. If not set, it defaults to `deepseek-chat`.

```php
$deepseek->model('deepseek-chat');
```

### Setting the Role

You can set the role for the chat. Available roles are `user`, `assistant`, and `system`. The default role is `user`.

```php
$deepseek->role('user');
```

### Sending a Prompt

To send a text prompt and receive a response:

```php
$response = $deepseek->chat("Hello, how are you?");
echo $response;
```

### Streaming Responses

For streaming responses, you can pass a callback function or set the stream parameter to `true`.

#### Using a Callback Function

```php
$deepseek->chat("Tell me a story.", function($token, $done) {
    if ($done) {
        echo "\nStream complete.\n";
    } else {
        echo $token;
    }
});
```

#### Printing Stream Directly

```php
$deepseek->chat("Explain the theory of relativity.", true);
```

## Error Handling

The class throws exceptions for errors such as missing API keys, invalid roles, and API connection issues. Ensure to handle these exceptions in your code.

```php
try {
    $response = $deepseek->chat("Hello, how are you?");
    echo $response;
} catch (Exception $e) {
    echo 'Error: ' . $e->getMessage();
}
```

## Example Usage

Here is a complete example demonstrating the usage of the `DeepSeek` class:

```php
require_once 'path/to/DeepSeek.php';

$deepseek = new DeepSeek();
$deepseek->key('your-api-key-here');

try {
    $deepseek->model('deepseek-chat');
    $deepseek->role('user');
    $response = $deepseek->chat("What is the capital of France?");
    echo $response . "\n";

} catch (Exception $e) {
    echo 'Error: ' . $e->getMessage();
}
```

⭐ If you liked what I did, if it was useful to you, or if it served as a starting point for something more magical, let me know with a star 💚.
