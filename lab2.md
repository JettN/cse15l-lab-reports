# Lab 2

## Part 1: Webserver

My `StringServer` code:

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                if(message.equals("")){
                    message = parameters[1];
                    return String.format(message);
                }
                else{
                    message = message + "\n" + parameters[1];
                    return String.format(message);
                }
            }
        }
        return "404 Not Found!";
    }
}
class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

**Using `/add-message`**
![First message](local server 1st message.JPG](https://github.com/JettN/cse15l-lab-reports/blob/dc13296afc9b77d3b8c77a8a3489310128910eb6/local%20server%201st%20message.JPG)

When using `/add-massage`, the method `handleRequest(URI url)` is called. It handles a `URI` argument labeled `url`. The method `handleRequest(URI url)` is within the class `Handler` which implements `URLHandler`. In the `Handler` class, a String field called `message` exists which equals `""`, or an empty string. After using `/add-massage?s=How are you doing?`, `message` is updated to equal `"How are you doing?"`.

![Second Message](https://github.com/JettN/cse15l-lab-reports/blob/1804356e1e0115a1c841807baada4b2bcd229358/local%20server%202nd%20message.JPG)

When using `/add-message` again, the method `handleRequest(URI url)` is called. It handles a `URI` argument labeled `url`. The method `handleRequest(URI url)` is within the class `Handler` which implements `URLHandler`. In the `Handler` class, a String field called `message` exists which now equals `"How are you doing?"`, as the previous `/add-message` updated the `message` variable. After using `/add-massage?s=Fine. And you?`, `message` is updated to equal `"How are you doing?\nFine. And you?"`. `\n` indicates a new line, meaning that the webpage will show the messages as:

```
How are you doing?
Fine. ANd you?
```
