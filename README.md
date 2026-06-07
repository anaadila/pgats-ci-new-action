[![Code coverage badge](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://stryker-mutator.io/robo-coasters-example/reports/coverage/lcov-report/index.html)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fstryker-mutator%2Frobo-coasters-example%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/stryker-mutator/robo-coasters-example/master)

# PGATS - CI

## Pré-requisitos

1. Instale o [git](https://git-scm.com)
2. Instale o [nodejs](https://nodejs.org/)
3. Instale o Yarn - `npm install -g yarn`
4. Faça um _Fork_ do projeto
5. Clone o repositório para sua máquina (seu fork)
6. Instale as dependências
   ```shell
   cd pgats-ci
   yarn
   ```
7. Execute os testes de unidade - isso vai gerar um relatório
   ```shell
   yarn run test
   ```
8. Abra o relatório de cobertura de código em `reports/coverage/lcov-report`
9. Execute os testes de mutação com o Stryker
   ```shell
   yarn run test:mutation
   ```
10. Abra o relatório de mutação em `reports/mutation`
11. Instale os navegadores do Playwright
    ```shell
    yarn playwright install
    ```
12. Execute os testes end-to-end com o Playwright
    ```shell
    yarn run e2e
    ```
13. Execute a aplicação com `yarn start`
14. Acesse a aplicação publicada [neste link](https://pgats-ci-example.netlify.app)

## Pipeline do GitHub Actions

O workflow principal está em `.github/workflows/pipeline.yaml` e executa as seguintes etapas:

- code quality com `MegaLinter`
- testes unitários com `yarn run test`
- testes de mutação com `yarn run test:mutation`
- testes E2E com `yarn run e2e`

### Detalhes do workflow

- Disparos suportados:
  - `push` na branch `master`
  - `pull_request` direcionado para `master`
  - `workflow_dispatch` manual
- O `workflow_dispatch` tem inputs configuráveis:
  - `run_mutation` para ativar/desativar testes de mutação
  - `run_megalint` para ativar/desativar MegaLinter
- O workflow usa `concurrency` para cancelar execuções anteriores do mesmo branch
- Artefatos de relatório são enviados para:
  - `megalinter-reports`
  - `unit-test-coverage`
  - `mutation-test-report`
  - `playwright-report`

> Localmente, use os mesmos comandos descritos acima. O workflow GitHub Actions reflete esse fluxo de validação.

---

💜⚡️
 
# pgats-ci