## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/JBBS7/RCE-jbbs/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

DATE: 23.10.2021      
IMPLEMENTATION OF REMOTE COMMAND EXECUTION (RCE)

AIM:
To implement Remote Command Execution(RCE). 

ALGORITHM:

CLIENT SIDE:-

1. Establish a connection between the Client and Server.
Socket client=new Socket("127.0.0.1",6555);
2. Create instances for input and output streams.
Print Stream ps=new Print Stream(client.getOutputStream());
3. BufferedReaderbr=newBufferedReader(newInputStreamReader(System.in));
4. Enter the command in Client Window.
Send themessage to its output
str=br.readLine();
ps.println(str);

SERVER SIDE:-

1. Accept the connection request by the client.
ServerSocket server=new ServerSocket(6555);
Sockets=server.accept();
2. Getthe IPaddressfromitsinputstream.
BufferedReaderbr1=newBufferedReader(newInputStreamReader(s.getInputStream()));
ip=br1.readLine();
3. During runtime execute the process
Runtime r=Runtime.getRuntime();
Process p=r.exec(str);

CODE:
CLIENT PROGRAM

import java.io.*;

import java.net.*; 

class clientRCE

{

public static void main(String args[]) throws IOException

{

try

{

String str;Socket client=new Socket("127.0.0.1",6555);

PrintStream ps=new PrintStream(client.getOutputStream());

BufferedReader br=new BufferedReader(new InputStreamReader(System.in));

System.out.println("\t\t\t\tCLIENT WINDOW\n\n\t\tEnter TheCommand:");

str=br.readLine();

ps.println(str);

}

catch(IOException e)

{

System.out.println("Error"+e); }

}}


SERVER PROGRAM

import java.io.*;

import java.net.*;

class serverRCE

{

public static void main(String args[]) throws IOException

{
 try
 
{
String str;

ServerSocket server=new ServerSocket(6555);

Socket s=server.accept();

BufferedReader br=new BufferedReader(new InputStreamReader(s.getInputStream()));

str=br.readLine();

Runtime r=Runtime.getRuntime();

Process p=r.exec(str);
}
catch(IOException e)

{
System.out.println("Error"+e);

}}}



OUTPUT

![image](https://user-images.githubusercontent.com/94218612/142985144-97016561-0063-4f9d-ac50-2130e0dc4426.png)


RESULT

Thus the implementation RCE is done & executed successfully.


### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
