pipeline
{
  agent any
  stages
  {
    stage('Checkout')
    {
      steps
      {
        echo 'Pulling code from Github'
        checkout scm
      }
    }
    stage('Bulid')
    {
      steps
      {
        echo 'Buliding project is going on'
        bat 'echo Bulid completed successfully '
      }
    }
    stage('Validation Check')
    {
      steps
      {
        echo 'Validating project readiness'
        bat '''
        findstr READY=true check.txt > nul
        if errorlevel 1 (
          echo  Validation Failed
          exit 1
        )
        else
        (
          echo Validation passed
        )
        '''
      }
  }
    stage('Manager Approval')
    {
      steps
      {
        input message : 'Approve deployment?' ok :'Approve'
      }
    }
    stage('Ready for Deployment')
    {
      steps {
        echo 'deployment approved  and ready '
      }
    }
}
}
