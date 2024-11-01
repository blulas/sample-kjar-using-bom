# IBM Business Automation Manager Open Editions - KJAR Sample (with BOM)
This repository contains a sample KJAR for use with BAMOE v8.0.6.  This sample demonstrates how to properly use the Maven Bill-of-Materials (BOM) in order to properly manage the varous versions of BAMOE's libraries.

## Overview
The purpose of this repository is to guide the developer through the setup and use of BAMOE v8.  The `first step` is to make sure you local development environment or workstation is configured with the proper developer tooling, frameworks, and runtimes.  Once your development environment is configured, you can proceed to the remaining steps to create the project, add assets and unit tests, and deploy your solution.

## Tool & Environment Requirements
The following tools and frameworks are required to be installed on the developer workstation.  Please follow the link in order to download and install the various tools:
- [**JDK 11**](https://developer.ibm.com/languages/java/semeru-runtimes/downloads/), prefer the IBM Semeru release of JDK 11, but any OpenJDK will do
install any GIT related extensions or simply use the command line tools
- [**GIT Command Line Interface**](https://git-scm.com/downloads), plus you are free to install any GIT related extensions or simply use the command line tools- [**Maven Command Line Interface**](https://maven.apache.org/install.html), used for builds and deployments of BAMOE libraries, plus you are free to install any Maven related extensions or simply use command line tools.
- [**VS Code IDE**](https://code.visualstudio.com/download), and install the following extensions from the VS Code Marketplace:
BAMOE Developer Tools, this is the set of editors for DMN, BPMN, and PMML that developers use to create their visual models in the IDE Drools (by Jim Moody), this is a third-party editor which does simple syntax highlighting of the Drools Rule Language (DRL) files

## Maven Settings

In order to be able to build this sample, you must have your Maven `settings.xml` file updated to access the libaries, either via the published Maven repository or via the local/offline version.  The `settings.xml` file located in this sample's `maven` folder includes a sample for your use.

```xml
<settings xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://maven.apache.org/SETTINGS/1.0.0" xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">

    <localRepository>${user.home}/.m2/repository</localRepository>
    <profiles>
        <!-- BAMOE v8 via Public Maven (Red Hat) -->
        <profile>
            <id>ibm-bamoe-v8-maven-repository</id>
            <repositories>
                <repository>
                    <id>ibm-bamoe-v8-maven-repository</id>
                    <url>https://maven.repository.redhat.com/ga/</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </repository>
            </repositories>

            <pluginRepositories>
                <pluginRepository>
                    <id>ibm-bamoe-v8-maven-repository</id>
                    <url>https://maven.repository.redhat.com/ga/</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </pluginRepository>
            </pluginRepositories>
        </profile>

        <!-- BAMOE 8.0.6 via Offline -->
        <profile>
            <id>ibm-bamoe-806-offline-maven-repository</id>
            <repositories>
                <repository>
                    <id>ibm-bamoe-806-offline-maven-repository</id>
                    <url>file:///Users/${USER}/.m2/bamoe-8.0.6.GA-maven-repository</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>ibm-bamoe-806-offline-maven-repository</id>
                    <url>file:///Users/${USER}/.m2/bamoe-8.0.6.GA-maven-repository</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                    </pluginRepository>
            </pluginRepositories>
        </profile>
    </profiles>

    <activeProfiles>
        <activeProfile>ibm-bamoe-v8-maven-repository</activeProfile>
        <activeProfile>ibm-bamoe-806-offline-maven-repository</activeProfile>
    </activeProfiles>
</settings>
```

## Running Container Images Locally
There are several pre-built container images which assist the developer.  These images require a container management system, such as **Docker**, **PodMan**, or **Rancher Desktop**.  Most BAMOE technologists use **Rancher Desktop**, which can be run in `docker` mode, and we can supply a startup repository that installs Canvas and other images into your Rancher installation.  If you plan to install the container images on your laptop, we will also guide you through this, but here are the instructions if you want to get ahead.  

## How To Build
Once you have configured your local development environment, you need to perform a `Maven Build` of the repository.  This repository is built using `mvn clean install` by either the CI/CD pipeline or on a local developer workstation.  If deploying artifacts to an enterprise Maven repository, please use `mvn clean deploy`, which requires configuration of the `distributionManagement` section of your project's parent pom.xml.

## Additional Information (*Appendicies*)
This repository is focused on business automation using the **IBM Business Automation Manager Open Editions** product, which in turn relies on various open source tools and technology. The following online documentation is available in order to learn various aspects of these tools:

- [**Apache Maven**](https://maven.apache.org/) is a free and open source software project management and comprehension tool. Based on the concept of a project object model (POM), Maven can manage a project’s build, reporting and documentation from a central piece of  information. A **getting started guide** is available [here](http://maven.apache.org/guides/getting-started/).
- [**Git**](https://git-scm.com//) is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. There is a **handbook** available [here](https://guides.github.com/introduction/git-handbook/), as well as various **guides** for learning and working with Git available [here](https://guides.github.com/
business logic lives these days. By taking advantage of the latest technologies (Quarkus, knative, etc.), you get amazingly fast boot times and instant scaling on orchestration platforms like Kubernetes.
- [**IBM Business Automation Manager Open Editions**](https://www.ibm.com/docs/en/ibamoe) `IBM Business Automation Manager Open Editions`, which consists of `IBM Process Automation Manager Open Edition` and `IBM Decision Manager Open Edition`, offer developers the ability to build cloud-native applications that automate business operations. `IBM Process Automation Manager Open Edition` is a platform for developing containerized microservices and applications that automate processes and business decisions. `IBM Decision Manager Open Edition` is a separately available platform for developing containerized microservices and applications that automate business decisions, business rules, and complex event processing.
