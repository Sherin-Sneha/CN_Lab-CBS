Sherin Sneha J - 311119205051

_CONTENT BEYOND SYLLABUS_
**IMPLEMENTATION OF REMOTE COMMAND EXECUTION (RCE)**

_**AIM**_
To implement Remote Command Execution(RCE).

_**ALGORITHM**_
**CLIENT SIDE**
1. Establish a connection between the Client and Server.
Socket client=new Socket("127.0.0.1",6555);
2. Create instances for input and output streams.
Print Stream ps=new Print Stream(client.getOutputStream());
3. BufferedReaderbr=newBufferedReader(newInputStreamReader(System.in));
4. Enter the command in Client Window.
Send themessage to its output
str=br.readLine();
ps.println(str);

**SERVER SIDE**
1. Accept the connection request by the client.
ServerSocket server=new ServerSocket(6555);
Sockets=server.accept();
2. Getthe IPaddressfromitsinputstream.
BufferedReaderbr1=newBufferedReader(newInputStreamReader(s.getInputStream()));
ip=br1.readLine();
3. During runtime execute the process
Runtime r=Runtime.getRuntime();
Process p=r.exec(str);

**CLIENT PROGRAM**
```markdown
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
}
}
```

**SERVER PROGRAM**
```markdown
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
}
}
}
```

**_OUTPUT_**
![image](https://user-images.githubusercontent.com/67852150/142240284-66ed3c38-ce8a-4e5a-a96e-b105c685e70b.png)

_**RESULT**_
Thus the implementation RCE is done & executed successfully.
