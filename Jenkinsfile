node('master') {

  stage('Prep') {
    checkout scm
    sh "rm -rf penv && virtualenv penv"
    sh "penv/bin/pip install pytest pytest-cov pylint"
    sh "penv/bin/pip install -e ."
  }

  stage('Lint') {
    sh "penv/bin/pylint --exit-zero shlib"
  }

  stage('Test') {
    sh "penv/bin/pytest --cov=shlib --cov-report=term tests"
  }

  stage('Publish') {
    if(env.BRANCH_NAME == 'master') {
      // TODO
      echo "Publishing artifacts"
    } else {
      echo "Not publishing artifacts from a feature branch"
    }
  }

}

