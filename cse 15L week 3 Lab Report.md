# Minyan Shi's CSE 15L Week 1 Lab Report
---
# Part 1
---
## Code For Simplest Search Engine
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {

    String s = " ";
    public String handleRequest(URI url) {
        
         if (url.getPath().equals("/")) {
            return "String is now:" + s;
        } 
        else if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    s += parameters[1] + " ";
                    return ("List of string is now:" + s);
                }
            return "Not a String!";
        }
        else if (url.getPath().contains("/search")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                if(s != null){
                    String[] StringArr = s.split(" ");
                    String selectedString = "";
                    for(int i = 0; i < StringArr.length; i++) {
                        if(StringArr[i].contains(parameters[1])){
                            selectedString += " " + StringArr[i];
                        }
                    }
                    return ("Strings contains " + parameters[1] + " are:" + selectedString);
                }
            }
        return "Not a String!";
        }
        else{
            return "404 Not Found!"; 
        } 
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port string!");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

```
1. Return Current String Method <br />
<img width="947" alt="Week 3 Lab Screen Shot 0 1" src="https://user-images.githubusercontent.com/114315303/195947877-7c7de214-9dab-4fc1-8bbd-be3f7958263c.png">
In this screenshot we seen ("/") as the input arguement, which ask the handleRequest method to retuen the current string (which is the String variable s and is now empty).<br />
<br />

2. Add Method <br />
<img width="948" alt="Week 3 Lab Screen Shot 0 2" src="https://user-images.githubusercontent.com/114315303/195948235-bb164249-4add-4ba3-be4e-ba7da63b10c8.png">
In this screenshot, we call the add string method. We seen ("anewstringtoadd") as the input arguement and add this string to String variable s. Therefore the current string (String variable s) is now: "anewstringtoadd".<br />
<br />

<img width="944" alt="Week 3 Lab Screen Shot 0 3" src="https://user-images.githubusercontent.com/114315303/195949256-9062609b-e360-43dc-a0c0-6f5e8a14055c.png">
In this screenshot, we seen ("pineapple") as the input arguement and add this string to String variable s. Therefore the current string (String variable s) is now: "anewstringtoadd pineapple".<br />
<br />

<img width="950" alt="Week 3 Lab Screen Shot 0 4" src="https://user-images.githubusercontent.com/114315303/195949338-25d5f663-9e2a-4c9e-8e97-e0d1017ecff2.png">
In this screenshot, we seen ("apple") as the input arguement and add this string to String variable s. Therefore the current string (String variable s) is now: "anewstringtoadd pineapple apple".<br />
<br />

3. Search Method <br />
<img width="949" alt="Week 3 Lab Screen Shot 0 5" src="https://user-images.githubusercontent.com/114315303/195949610-cbeb2431-fde8-4721-a89d-a17561bfd8d8.png">
In this screenshot, we seen ("app") as the input arguement and return all the element that contains "app" in the current string (String variable s). Therefore the return string is: "pineapple apple". <br />
<br />


---
# Part 2
---
## Array Method
1. The failure-inducing input and the symptom:
<img width="1110" alt="Week 3 Lab Screen Shots 1 2" src="https://user-images.githubusercontent.com/114315303/195725908-b2c7020d-b373-40c8-af55-88709927cef0.png">
The method reverseInPlace fail the test with {1,2,3,4} as input that we get {4,3,3,4} instead of the expected outcome {4,3,2,1}.<br />
<br />
<img width="1121" alt="Week 3 Lab Screen Shots 1 3" src="https://user-images.githubusercontent.com/114315303/195725973-b80e65c8-843f-4062-b66b-ff48fd5728af.png">
The method reverse fail the test with {1,2,3,4} as input that we get {0,0,0,0} instead of the expected outcome {4,3,2,1}.<br />
<br />

2. The bug and Explainatino:
<img width="956" alt="Week 3 Lab Screen Shots 1 0" src="https://user-images.githubusercontent.com/114315303/195727291-4b6d0d3f-c7e0-430d-a10a-6162614d96c9.png">
The method reverseInPlace fail the test because of the command (arr[i] = arr[arr.length-i-1]). This command mirror the array by the middle of the array. It does reversed the entire array because those orginal values before the middle point of the array get changed without being stored. Using the input of the test {1,2,3,4} as an example, [1,2] has already been changed to [4,3] when we trying to pass their value to the later index. Value [1,2] does not get stored and can not be find later. Therefore, with this method we are unable to pass the orginal values before the midpoint to index after the mid point. <br />
<br />

The method reverse fail the test because of the command (arr[i] = newArray[arr.length-i-1]) and (return arr). The command (arr[i] = newArray[arr.length-i-1]) let arr[i] equal to the defalt value 0 and (return arr) will return an array with value 0 at every index. After create (int[] newArry) with the same length as the input arguement (int[] arr) and the defalt value 0 for each element in the newArry, we should let (newArray[arr.length - i - 1] = arr[i]), passing the value from the back of the (arry) to the (newArry). After updating the value on each index of the (newArray) we should return (newArray) which is an array with the reversed value of the (arry). <br />
<img width="1101" alt="Week 3 Lab Screen Shots 1 4" src="https://user-images.githubusercontent.com/114315303/195731356-f78ebbc8-3269-4fc7-86c8-5b5b22ccab6a.png">
(Then we can pass the test.)


## LinkedList Method
1. The failure-inducing input and the symptom:
<img width="1086" alt="Week 3 Lab Screen Shots 2 1" src="https://user-images.githubusercontent.com/114315303/195762600-8b53b077-66e3-4889-b352-c287eba7bf2b.png">
The method append fail the test after append ([1,2,3]) to an empty LinkedList object that we get a OutOfMemoryErro instead of the expected outcome that the third node has value 3.<br />
<br />

2. The bug and Explainatino:
<img width="1098" alt="Week 3 Lab Screen Shots 2 2" src="https://user-images.githubusercontent.com/114315303/195764431-25011adc-665d-41b1-a695-987b1bc49895.png">
The method append fail the test since we add more than one element and the while loop to operate the appending process is massed up. The while loop actually never stop. Using the test input as an example, after add value (1) and (2), Node n = this.root equals Node(1,Node(2,null)). Therefore, n.next = Node (2,null) which isn't null. Since it doesn't not violate the while statement, we next go into the while loop for the third append. Now, in the while loop, with the command (n = n.next), we update n to equal the Node(2,null) and then update n.next to equal Node(3,null). Here is the problem that now n.next is equal to Node(3,null) which isn't null. As the while statement is always true, it will be an infite loop, adding Node(3,null) untill we outof memory.
<img width="927" alt="Week 3 Lab Screen Shots 2 3" src="https://user-images.githubusercontent.com/114315303/195772560-b83972c6-ccfe-4ef4-8234-fd662ff18ba3.png">
(the bug will be fixed after moving the appending command n.next = new Node(value,null) out of the while loop)
---
