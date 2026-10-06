# Estratégia de Branches

Para este projeto, adotaremos o modelo **Panic Branchs**.
Esta estratégia combina a simplicidade de uma única branch principal com um processo de lançamento controlado para o ambiente de produção. O modelo se alinha aos requisitos de Integração Contínua (CI) e às políticas do time, como a Definition of Ready (DoR) e a Definition of Done (DoD).

A filosofia é simples: a branch `main` representa o código mais atual e já validado, enquanto o ambiente de produção é atualizado apenas por meio de releases explícitas, geradas ao final de cada sprint.

### Fluxo de Trabalho

1. **Branch principal**

   - Utilizamos apenas uma branch de longa duração: `main`.
   - Ela só recebe código que passou por CI, code review, testes de sistema, aceite do PO e DoD.

2. **Branches de tarefa**

   - Cada tarefa técnica é desenvolvida em uma branch curta, criada a partir da `main`.
   - Os commits são frequentes, representam o escopo de uma tarefa, e a implementação inclui testes unitários.
   - Nomenclatura: 
        - `feat/nome-da-feature`
        - `fix/nome-do-bug`

3. **Pull Requests (PRs)**

   - Ao concluir a implementação, abre-se um **PR** da branch da tarefa para a `main`.
   - A abertura do PR dispara a pipeline de CI (build, lint, testes unitários e de integração). Se a CI falhar, a tarefa volta para a implementação.
   - Com a CI aprovada, o código passa por **code review**, que verifica os critérios de aceitação e a política de testes. Se for reprovado, volta para a implementação.
   - Padrão de título e número mínimo de revisores: 
        - O título do PR deve conter o ID da tarefa correspondente (ex: [#321] Criação do banco de dados)
        - Devem contar com um revisor que não é o responsável direto pela task.

4. **Validação em Staging**

   - Após a aprovação no code review, e antes do merge na main, a **branch da tarefa** é publicada no ambiente de **staging**.
   - Nesse ambiente são executados os testes de sistema e o **aceite do Product Owner**.
   - Se houver reprovação, a tarefa volta para a implementação com um feedback.

5. **Merge na main**

   - Com a validação em staging aprovada, verifica-se se a entrega atende à **Definition of Done (DoD)**.
   - Se atender, a branch é integrada na `main`. Se não, volta para a implementação.

6. **Publicação em Produção**

   - Ao final da sprint, uma **release** é gerada a partir da `main`, com **tag de versão** e **changelog**.
   - O release candidate passa por testes de regressão e smoke test. Se falhar, o problema retorna ao fluxo de desenvolvimento.
   - Aprovado o release candidate, é feito o deploy em produção, seguido de um **health check**.

7. **Rollback e Hotfixes**

   - Se o health check falhar, é feito **rollback** para a versão anterior.
   - Em seguida, realiza-se a análise de causa e a correção (**hotfix**), que segue o mesmo fluxo das demais tarefas: nova branch a partir da `main`, PR, CI, code review, validação em staging e nova release.

---

* Se o staging recebe também a `main` automaticamente após o merge, ou apenas as branches de tarefa.

