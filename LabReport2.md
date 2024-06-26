## Part 1

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

# What methods were being called?
main method of ChatServer: Initializes the server.
handleRequest of Handler: Processes the incoming request.


# What are the relevant arguments to those methods, and the values of any relevant fields of the class?
handleRequest receives an URI object with a URI such as new URI("http://localhost:port/add-message?s=hello&user=Edwin").   
Relevant fields: num (remains 0 since it is not used in this specific handling), userInfo, and message.  
userInfo and message would change based on the parameters of the query. For the given URL, userInfo would be "Edwin" and message would be "hello".  

# How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
userInfo changes to "Edwin" and message to "hello" for the first request.  
For a second request,the parameters may be changed, e.g., /add-message?s=goodbye&user=Jane. Here, userInfo would update to "Jane" and message to "goodbye".  

# Screenshot 

![image](https://github.com/Xnyi8830/CSE15L/blob/main/Screenshot%202024-05-04%20at%205.41.35%20PM.png)
![image](https://github.com/Xnyi8830/CSE15L/blob/main/Screenshot%202024-05-05%20at%207.08.28%20PM.png)


# Part 2

This is where my private key is stored.
![image](https://github.com/Xnyi8830/CSE15L/blob/main/Screenshot%202024-05-06%20at%208.21.03%20PM.png)  

This is where my public key is stored.  
![image](https://github.com/Xnyi8830/CSE15L/blob/main/Screenshot%202024-05-06%20at%208.24.57%20PM.png)

This is my terminal interactions.
![image](https://github.com/Xnyi8830/CSE15L/blob/main/Screenshot%202024-05-06%20at%208.27.36%20PM.png)


# Part 3
We learned about how to access server. I have never been learned how a server is accessed and how to directly visualize my code through a webpage, and thus learning about them was super helpful. 
