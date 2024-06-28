What is Jenkins?
    - Story of  Jenkins and Hudson.
    - Jenkins is a Java Web Application.
    - Open source automatin server
    - Continuos Integration , Plugins , Easy configuration , Extensible.
    -  By default,Jenkins home directory is  .jenkins, and will be placed in your home directory.
    -  one can change home directory by defining JENKINS_HOME environment variable.
    - 
    Manage Jenkins...
    - Configure System Configuration :
                        -Home Directory: /var/jenkins_home
                        -No. of Executors:   manage paths to various tools used in build.
                        -Quiet Period: newly triggered builds of this project will be added to the queue, but Jenkins will wait for the specified period of time (in seconds) before actually starting the build.
                                      - to ensure that the build always uses a stable source code version.

    - Maven : high level build scripting framework for Java to use standard directory , standaard life cycle, 
                -  Dependency management: (Maven helps project dependencies in standardasied way.)
                                           (ensures all necessary libraries for building the project.)
                -  Standardise Project structure
                - Build lifecycle(phases like compile, test, package, and deploy)
                - Plugins (wide range of plugins (compiling code, running tests, generating reports)
                - Integration with Jenkins (Jenkins provides a Maven plugin that integrates Maven projects.)

    - Ant : in Jenkins
            - Build scripts ==> nt uses XML-based build scripts to define the build process
            - Task execution : wide range of built-in tasks (e.g., javac for compiling Java code, junit for running tests)
            - Integrates with Jenkins : directly execute from jenkins
    

    Pipeline in Jenkins
    pipeline {
        agent { ①  label '' }
        
        stages{  

            stage('Build') { ②
                steps { ③
                    sh 'make' ④
                    }
                }

            stage('Test'){
                steps {
                    sh 'make check'
                    junit 'reports/**/*.xml' ⑤
                    }
                }

            stage('Deploy') {
                steps {
                    sh 'make publish'
                    }
                }
        }
}

1 agent---> indicates that Jenkins should allocate an executorand workspace
2 stage---> describes stage of pipeline
3 steps---> describes steps  to run in this stage
4 sh -----> executes shell command
5 Junit---> Pipeline step provided by JUnit Plugin


Scripted Pipeline
- more traditional way ,  using Groovy scripting language
- Flexibility  -Custom Logic  -Programmatic Approach
// Script //
node {
    try {
        stage('Build') {
            echo 'Building...'
            // Your build steps here
        }
        stage('Test') {
            echo 'Testing...'
            // Your test steps here
        }
        stage('Deploy') {
            echo 'Deploying...'
            // Your deploy steps here
        }
    } catch (Exception e) {
        echo "Caught: ${e}"
        currentBuild.result = 'FAILURE'
    } finally {
        echo 'This always runs'
    }
}


Difference between declaratie and scripted
Syntax and Structure:
            Declarative pipelines --rigid and simple structure, 
            Scripted pipelines --offer more flexibility and are more powerful but more complex.

Ease of Use:
            Declarative pipelines are easier to use, especially for those new to Jenkins and CI/CD. 
            Scripted pipelines are better for complex and advanced use cases.
Error Handling:
            Declarative pipelines have built-in error handling through post blocks, making it easier to manage post-build actions.
            Scripted pipelines require manual try-catch blocks for error handling.


More info:https://www.jenkins.io/doc/book/pipeline/syntax/












                        
                    

