pipeline {
    agent any

    stages {
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
                echo 'Test Step: Running pytest'

                # Initialize conda
                source /home/hdng/miniconda3/etc/profile.d/conda.sh

                # Create and activate environment (if it doesn't exist)
                conda create -n mlip python pytest numpy pandas scikit-learn -c conda-forge -y || true
                conda activate mlip

                # Run pytest
                pytest
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
