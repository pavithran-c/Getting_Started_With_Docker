# Task 5

## Install Maven
```bash
sudo apt install maven
```
![alt text](<./output_day5/Screenshot from 2025-03-21 16-07-24.png>)

## Fork the repo on github

![alt text](./output_day5/image.png)

## Configure Jenkins
 - In Jenkins go to `configure jenkins` > `tools`
 - Locate JDK section
 - Uncheck `Install Automatically`
 - Name `Java 17`
 - Go to terminal and enter the command and get the java 17 path:

```bash
update-java-alternatives --list 
```

 - paste the java path in `JAVA_HOME`

![alt text](<./output_day5/Screenshot from 2025-03-21 16-07-24-1.png>)

## Fork The Repo and build the pipeline
![alt text](<./output_day5/image (1).png>)
