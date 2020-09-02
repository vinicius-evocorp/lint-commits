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

  ## 1   - CRIAR UMA PASTA VAZIA
    mkdir lintcommit
  ## 2   - ACESSAR A PASTA CRIADA
    cd lintcommit
  ## 3   - INICIALIZAR UM REPOSITORIO VAZIO DO GIT
    git init
  ## 4   - INICIAR O NODE
    yarn init -y
  ## 5   - ABRIR O PROJETO NO VSCODE
    code .
  ## 6   - INSTALAR O commitlint cli e a configuracao do conventional
    yarn add @commitlint/config-conventional @commitlint/cli -D
  ## 7   - CONFIGURAR O COMMITLINT P/ USAR A CONFIGURAÇÃO DO CONVENTIONAL 
    `echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js`
  ## 8   - ADD O HUSKY P/ INFORMAR PRO COMMITLINT QUE ELE PRECISA SER EXECUTADO DEPOIS DO COMMIT (`git commit`)
    yarn add husky -D
  ## 9   - CRIAR UM ARQUIVO `.gitignore` e colocar a pasta `node_modules` nele
  ## 10  - ADICIONAR NO `package.json` A CONFIGURAÇÃO DO HUSKY
      "husky": {
        "hooks": {
          "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
        }
      }
  ## 11  - P/ TESTAR SE ESTAR FUNCIONANDO, DE UM COMMIT
    git add .
    git commit -m "Initial commit"
  ## 12  - DEU ERRO!!! CORRIJA A MENSAGEM DE COMMIT
    git commit -m "feat(backend): add initial setup"
  ## 13  - VERIFICAR OS LOGS DO GIT P/ VER O COMMIT REALIZADO
    git log
  ## 14  - ADD O COMMITZEN
    yarn add commitizen -D
  ## 15  - EXECUTAR O COMANDO P/ INICIAR O COMMITZEN
    yarn commitizen init cz-conventional-changelog --yarn --dev --exact
  ## 16  - INICIAR O COMMITZEN
    yarn commitzen init
  ## 17  - CONFIGURAR P/ EXECUTAR O COMMITZEN SER EXECUTADO SEMPRE QUE DER UM `git commit`
      "husky": {
        "hooks": {
          ...
          "prepare-commit-msg": "exec < /dev/tty && git cz --hook || true"
        }
      }
  ## 18  - AGORA É SO DAR UM NOVO COMMIT E ESTARA FUNCIONANDO... OU NÃO!
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
  ##  ATENCAO: Lembre-se de dar um git init antes de instalar o husky, para funcionar corretamente.

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
