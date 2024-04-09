## Desafio de teste no front com cypress (by Erick Wendel)

Esse desafio foi proposto pelo Erick Wendel nesse vídeo:
[https://www.youtube.com/watch?v=56N0P67ffIA](https://www.youtube.com/watch?v=56N0P67ffIA)

Hoje, dia 09 de abril de 2024, eu implementei a primeira parte que está no vídeo.
Tive que fazer algumas mudanças para que funcionasse corretamente pois estou usando uma estrutura de pastas diferente e
isso gerou o erro abaixo no github actions:

```
Run npm run cypress:headless

> teste-e2e@1.0.0 cypress:headless
> npx cypress run --browser electron

The cypress npm package is installed, but the Cypress binary is missing.

We expected the binary to be installed here: /home/runner/.cache/Cypress/13.7.2/Cypress/Cypress

Reasons it may be missing:

- You're caching 'node_modules' but are not caching this path: /home/runner/.cache/Cypress
- You ran 'npm install' at an earlier build step but did not persist: /home/runner/.cache/Cypress

Properly caching the binary will fix this error and avoid downloading and unzipping Cypress.

Alternatively, you can run 'cypress install' to download the binary again.

https://on.cypress.io/not-installed-ci-error

---

Platform: linux-x64 (Ubuntu - 22.04)
Cypress Version: 13.7.2
Error: Process completed with exit code 1.


```

Para resolver o problema adicionei a action abaixo:

```
- name: Run Cypress install
        run: node_modules/cypress/bin/cypress install
        working-directory: .
```
