# Lab Report 2  
## Part 1: StringServer
```
//StringServer.java 
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> stringList = new ArrayList<>();

    public String handleRequest(URI url) {
        System.out.println("Path: " + url.getPath());
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                    stringList.add(parameters[1] + "\n");
            }
        }
        if(stringList.size() == 0){
            return String.format("Please use /add to add the first String!");
        }

        StringBuilder output = new StringBuilder();
        for(String s: stringList){
            output.append(s);
        }
        return String.format("%s\n",output);
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
**Note**: For StringServer.java to operate, I needed to import the Server.java file that Joe Politz gave us from wavelet. 
