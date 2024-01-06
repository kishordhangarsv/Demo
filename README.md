
1. **Agent Declaration:**
   
   agent any
   
   - This declares that the pipeline can run on any available agent (Jenkins node/agent). The keyword `any` means that the pipeline can run on any available executor.


*******************************************************************************************************

3. **Stages:**
   stages {
       stage('Build') {
           steps {
               // Steps for the 'Build' stage
           }
       }
   }

   - This section defines the stages of the pipeline. In this case, there is one stage named 'Build.'


*******************************************************************************************************

4. **Build Stage:**

   steps {
       // Checkout your source code from the Git repository and use the 'main' branch
       git branch: 'main', url: 'https://github.com/kishordhangarsv/Demo.git'
       // Build your Java program
       sh 'javac -d . Helloworld.java'
       // Run your Java program (assuming it has a main class)
       sh 'java -cp . Helloworld'
   }

   - This stage consists of three steps:
      - **Checkout Step:**
        - It checks out the source code from the specified Git repository       
         (`https://github.com/kishordhangarsv/Demo.git`) and uses the 'main' branch.

      - **Build Step:**
        - It compiles the Java program (`Helloworld.java`) using the `javac` command.
          
      - **Run Step:**
        - It executes the compiled Java program using the `java` command.


*******************************************************************************************************

5. **Post Section:**
   post {
       always {
           cleanWs()
       }
   }
   ```
   - This section defines post-build actions. In this case, it always runs the `cleanWs()` step, which cleans up the workspace after the build. The `always` block ensures that this step is executed regardless of the build result.

To use this Jenkinsfile:

1. Create a new pipeline job in Jenkins.
2. In the job configuration, select "Pipeline script" and paste the content of the Jenkinsfile into the script editor.
3. Save the configuration.
4. Run the Jenkins job, and it will execute the defined stages, checking out the Git repository, compiling the Java program, and running it.

*******************************************************************************************************
    
    
   ** Jenkinsfile**
   
   pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Checkout your source code from the Git repository and use the 'main' branch
                git branch: 'main', url: 'https://github.com/kishordhangarsv/Demo.git'
                // Build your Java program
                sh 'javac -d . Helloworld.java'
                // Run your Java program (assuming it has a main class)
                sh 'java -cp . Helloworld'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}


*******************************************************************************************************

    ![image](https://github.com/kishordhangarsv/Demo/assets/151608869/a4ea8dbf-d380-46a3-a032-0ea6e58315e3)

 
*******************************************************************************************************   
  
    
    **Console Output**

    
Started by user Devops Lover
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/jenkins_workspace
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/kishordhangarsv/Demo.git
 > git init /var/lib/jenkins/workspace/jenkins_workspace # timeout=10
Fetching upstream changes from https://github.com/kishordhangarsv/Demo.git
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/kishordhangarsv/Demo.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/kishordhangarsv/Demo.git # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision d3ef97846311e065d350d75c73d5fbb4f0efc270 (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f d3ef97846311e065d350d75c73d5fbb4f0efc270 # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git checkout -b main d3ef97846311e065d350d75c73d5fbb4f0efc270 # timeout=10
Commit message: "Update Helloworld.java"
 > git rev-list --no-walk 99d865533ca69b60c5ad88b0b6d9eba31fc4b974 # timeout=10
[Pipeline] sh
+ javac -d . Helloworld.java
[Pipeline] sh
+ java -cp . Helloworld
Hello, Jenkins Pipeline!
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Declarative: Post Actions)
[Pipeline] cleanWs
[WS-CLEANUP] Deleting project workspace...
[WS-CLEANUP] Deferred wipeout is used...
[WS-CLEANUP] done
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS











