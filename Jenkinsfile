pipeline {
    agent any

    stages {
        stage('Setup Environment') {
            steps {
                sh '''
                #!/bin/bash
                # Check if the conda environment exists
                if [ $(conda env list | grep lab6-sgangrad | wc -l) -eq 0 ]; then
                    echo "Creating Conda environment: lab6-sgangrad"
                    # Create a new conda environment
                    conda create -y -n lab6-sgangrad python=3.8 pytest -c conda-forge
                else
                    echo "Conda environment 'lab6-sgangrad' already exists"
                fi
                '''
            }
        }
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo 'In C or Java, we can compile our program in this step'
                echo 'In Python, we can build our package here or skip this step'
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                echo 'Test Step: We run testing tool like pytest here'

                # TODO fill out the path to conda here
                #sudo /opt/conda/bin/conda init bash
                # sudo /PATH/TO/CONDA init

                # Initialize Conda in bash
                eval "$(conda shell.bash hook)"
                
                # Activate the Conda environment
                conda activate lab6-sgangrad
        
                # Run pytest
                pytest

                # TODO Complete the command to run pytest
                sudo /opt/conda/bin/conda run -n mlip pytest
                # sudo /PATH/TO/CONDA run -n <Envinronment Name> <Command you want to run>

                echo 'pytest not runned'
                exit 1 #comment this line after implementing Jenkinsfile
                '''

            }
        }
        stage('Deploy') {
            steps {
                echo 'In this step, we deploy our porject'
                echo 'Depending on the context, we may publish the project artifact or upload pickle files'
            }
        }
    }
}
