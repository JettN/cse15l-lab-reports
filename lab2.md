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