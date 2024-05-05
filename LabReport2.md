```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;

    public String handleRequest(URI url) {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("&"); //it should only be query
                String UserInfo = "";
                String message = "";
                if (parameters.length == 2){
                    for (String i: parameters){
                        String[] content = i.split("=");
                        //it would always be in the format of s=hello&user=Edwin 
                        if (content[0].equals("user")){
                            UserInfo = content[1];
                    }   
                        if (content[0].equals("s")){
                            message = content[1];
                        }
                    }    
            } 
            String printString = UserInfo + ": " + message + "\n";
            return printString;
            }
        return "404 not found";
    }
}

class ChatServer {
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

**What methods were being called?**

>main method of ChatServer: Initializes the server.
>handleRequest of Handler: Processes the incoming request.
