node {
  checkout scm

  stage 'Deploy application release'
  writeFile file: 'extras.json', text: "{'image_tag':'${IMAGE_TAG}','ecs_tasks':[${TASKS}]}"
  withEnv(["VAULT_PASSWORD=${VAULT_PASSWORD}", "AWS_DEFAULT_REGION=us-east-2"]) {
    sh 'ansible-playbook site.yml -vvv --vault-password-file vault.py -e "@extras.json"'
  }
}