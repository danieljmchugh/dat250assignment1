# Java installation
As I have already worked a little with Java on this system, a version of the SDK has been installed. A quick `java -version` showed build version 18 is installed. The binaries are found in `urs/bin/` which is `$PATH`.

# IDE
As a personal preference, I enjoy programming with code editors rather than IDEs. Therefore I have opted to use VS Code.

# Gradle
As I am working on a MacOS laptop and have used homebrew in the past, I installed gradle version 8.3 using `brew install gradle` and verified its installation with `gradle -v`

# Git
As I am working on a MacOS laptop so git is installed with version 2.37.1

# Containers
I have gone for the recommended options of using podman. Installation of podman was also done agian through homebrew. After installtion, I tested `podman machine init` and `podman machine start` to start the VM, which gave a return message of `Machine "podman-machine-default" started successfully`.
Finally the installtion was verified within using `podman info` which gave version info 4.6.1

A DockerHub account was also created, username `danieljmc`

# Exercise: Make an application production-ready

1) Created repository on github and cloned it locally.
2) Ran gradle and set up the build system according to provided settings
		Project name: dat250exp1
		Source package: no.hvl.dat250.exp1
		Target version of Java: 18
3) Ran the commands:

		./gradlew check
		./gradlew build
		./gradlew run 
Which resulted in a succesful build and the output of `Hello World!` by the generated App.java class.