pipeline {
    agent any

    environment {
        TARGET_FILE = "W:\\Downloads\\1.txt"
        TARGET_DIR  = "W:\\Downloads"
    }

    stages {

        stage('1 - Validate Agent') {
            steps {
                bat 'echo Running on %COMPUTERNAME%'
            }
        }

        stage('2 - Verify Directory Exists') {
            steps {
                bat '''
                    if not exist "%TARGET_DIR%" (
                        echo Directory does not exist: %TARGET_DIR%
                        exit /b 1
                    )
                    echo Directory exists.
                '''
            }
        }

        stage('3 - Ensure File Exists') {
            steps {
                bat '''
                    if not exist "%TARGET_FILE%" (
                        echo Creating file...
                        type nul > "%TARGET_FILE%"
                    )
                    echo File ready.
                '''
            }
        }

        stage('4 - Show File Before Append') {
            steps {
                bat '''
                    echo ---- BEFORE ----
                    type "%TARGET_FILE%"
                '''
            }
        }

        stage('5 - Append X') {
            steps {
                bat '''
                    echo X>>"%TARGET_FILE%"
                    echo Append complete.
                '''
            }
        }

        stage('6 - Validate Append') {
            steps {
                bat '''
                    findstr /C:"X" "%TARGET_FILE%" >nul
                    if errorlevel 1 (
                        echo Append validation failed.
                        exit /b 1
                    )
                    echo Append validated.
                '''
            }
        }

        stage('7 - Show Final File Content') {
            steps {
                bat '''
                    echo ---- AFTER ----
                    type "%TARGET_FILE%"
                '''
            }
        }
    }
}
