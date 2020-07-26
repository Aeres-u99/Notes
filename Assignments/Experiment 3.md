#### How to access Jenkins?

1. Open a web browser and point it to http://SERVER_IP:8080 (where SERVER_IP is the IP address of the hosting server).

2. You will then be prompted to copy and paste a password that was created during the Jenkins installation. To retrieve that password, go back to the terminal window and issue the command:

```

sudo less /var/lib/jenkins/secrets/initialAdminPassword
```

![Getting the password](../img/Devops-Study.Cheese_Thu-16Apr20_07.24.png)

![jenkins Unlock page](../img/Devops-Study.Cheese_Thu-16Apr20_07.26.png)

![Cat password pewpew](../img/Devops-Study.Cheese_Thu-16Apr20_07.31.png)

![jenkins Start Page](../img/Devops-Study.Cheese_Thu-16Apr20_07.27.png)

Choose suggested plugins and then

Create the first user

![Creation of user.](../img/Devops-Study.Cheese_Thu-16Apr20_07.41.png)

Set the deafult path and you will be set to roll with jenkins.

![First page](../img/Devops-Study.Cheese_Thu-16Apr20_07.42.png)

# Experiment 3

# Aim:

### Testing java applications on jenkins. (paramterised and non parameterised)

![Java Application testing](../img/Devops-Study.Cheese_Thu-16Apr20_07.44.png)

After correct configuration and proper build information

![Hello.java using Jenkins](../img/Devops-Study.Cheese_Thu-16Apr20_09.05.png)

### Java Parameterised.

![Java parameterised](../img/Devops-Study.Cheese_Thu-16Apr20_21.15.png)

![Build Environment Creation](../img/Devops-Study.Cheese_Thu-16Apr20_21.20.png)

Running the build.

![Running the build](../img/Devops-Study.Cheese_Thu-16Apr20_21.24.png)

### Executing python programs using jenkins.

![Python code](../img/Devops-Study.Cheese_Thu-16Apr20_09.28.png)

![Python Jenkins](../img/Devops-Study.Cheese_Thu-16Apr20_09.30.png)

![python code running](../img/Devops-Study.Cheese_Thu-16Apr20_09.31.png)

![Success](../img/Devops-Study.Cheese_Thu-16Apr20_09.32.png)
