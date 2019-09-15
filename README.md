# jenkins-test-samples
This repository cotains Jenkins job and pipeline samples. 

Pipeline concepts
- Pipeline
This is a user defined block which contains all the processes such as build, test, deploy, etc. It is a collection of all the stages in a Jenkinsfile. All the stages and steps are defined within this block. It is the key block for a declarative pipeline syntax.

Pipeline Syntax - 
pipeline {

}

- Node
A node is a machine that executes an entire workflow. It is a key part of the scripted pipeline syntax.

Node Syntax -
node {

}

There are various mandatory sections which are common to both the declarative and scripted pipelines, such as stages, agent and steps that must be defined within the pipeline. These are explained below:

- Agent
An agent is a directive that can run multiple builds with only one instance of Jenkins. This feature helps to distribute the workload to different agents and execute several projects within a single Jenkins instance. It instructs Jenkins to allocate an executor for the builds. A single agent can be specified for an entire pipeline or specific agents can be allotted to execute each stage within a pipeline. Few of the parameters used with agents are:

- Any
Runs the pipeline/ stage on any available agent.

- None
This parameter is applied at the root of the pipeline and it indicates that there is no global agent for the entire pipeline and each stage must specify its own agent.

- Label
Executes the pipeline/stage on the labelled agent.

- Docker
This parameter uses docker container as an execution environment for the pipeline or a specific stage. In the below example I’m using docker to pull an ubuntu image. This image can now be used as an execution environment to run multiple commands.

Agent Syntax - 
pipeline {
   agent {
     docker {
       image: ubuntu
     }
   }
}

- Stages
This block contains all the work that needs to be carried out. The work is specified in the form of stages. There can be more than one stage within this directive. Each stage performs a specific task. In the following example, I’ve created multiple stages, each performing a specific task.
pipeline {
   agent any
   stages {
         stage ('Build') {
         ...
         }
         stage ('TEST') {
         ...
         }
         stage ('QA') {
         ...
         }
         stage ('Deploy') {
         ...
         }
         stage ('Monitor') {
         ...
         }
   }
}

- Steps
A series of steps can be defined within a stage block. These steps are carried out in sequence to execute a stage. There must be at least one step within a steps directive. In the following example I’ve implemented an echo command within the build stage. This command is executed as a part of the ‘Build’ stage.
pipeline {
  agent any {
  stages {
        stage ('Build') {
              steps {
                echo 'Running build phase'
              }
        }
  }
  }
}

Further examples can be found here: https://www.edureka.co/blog/jenkins-pipeline-tutorial-continuous-delivery





