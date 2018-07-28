node (label: 'slave') {
  // define the secrets and the env variables
  def secrets = [
      [$class: 'VaultSecret', path: 'kv/example', secretValues: [
          [$class: 'VaultSecretValue', envVar: 'testing', vaultKey: 'foo']]
      ]
  ]

  // inside this block your credentials will be available as env variables
  wrap([$class: 'VaultBuildWrapper', vaultSecrets: secrets]) {
      sh 'echo $testing'
      sh 'echo $testing > example.txt'
      sh 'cat example.txt'
  }
}
