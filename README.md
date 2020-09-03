### PACKAGES

  ## commitlint
    é tipo um eslint pra padronizar mensagens de commit

  ## cz-cli
    é uma interface de linha de comando, um software que cria uma interface mais
    visual na hora de criar o commit. Ele cria um menu, por meios de perguntas, 
    e no final é montado automaticamente a mensagem de commit.

  ## husky
    O husky nos permite criar funcionalidados automatizadas baseado em comandos do GIT.


### PRATICA

  ## 1 - INSTALAR O commitlint cli e a configuracao do conventional
    yarn add @commitlint/config-conventional @commitlint/cli -D
  ## 2 - CONFIGURAR O COMMITLINT P/ USAR A CONFIGURAÇÃO DO CONVENTIONAL 
    echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
  ## 3 - ADD O HUSKY P/ INFORMAR PRO COMMITLINT QUE ELE PRECISA SER EXECUTADO DEPOIS DO COMMIT (`git commit`)
    yarn add husky -D
  ## 4 - ADD O COMMITZEN
    yarn add commitizen -D
  ## 5 - EXECUTAR O COMANDO P/ INICIAR O COMMITZEN
    yarn commitizen init cz-conventional-changelog --yarn --dev --exact
  ## 6 - INICIAR O COMMITZEN
    yarn commitizen init
  ## 7 - CONFIGURAR P/ EXECUTAR O COMMITZEN SER EXECUTADO SEMPRE QUE DER UM `git commit`
      "husky": {
        "hooks": {
          "commit-msg": "commitlint -E HUSKY_GIT_PARAMS",
          "prepare-commit-msg": "exec < /dev/tty && git cz --hook || true"
        }
      }
  ## 8 - AGORA É SO DAR UM NOVO COMMIT E ESTARA FUNCIONANDO... OU NÃO!
    git add .
    git commit

### REFERENCIES
  [https://www.youtube.com/watch?v=erInHkjxkL8] - ROCKETSEAT YOUTUBE 
  [https://github.com/conventional-changelog/commitlint]  - DOCUMENTATION COMMITLINT
  [https://commitlint.js.org/#/]  - COMMITLINT SITE
  [conventionalcommits.org/en/v1.0.0/]  - CONVEnTIONAL COMMITS
  [https://github.com/commitizen/cz-cli] - DOCUMENTATION COMMITZEN (cz-cli)

### OBS
  ##  O `commitlint changelog` foi criado pela comunidade do Angular. É o padrão utilizado pela maioria.

  ## Types commits
    `build`: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
    `ci`: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
    `docs`: Documentation only changes
    `feat`: A new feature
    `fix`: A bug fix
    `perf`: A code change that improves performance
    `refactor`: A code change that neither fixes a bug nor adds a feature
    `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
    `test`: Adding missing tests or correcting existing tests
