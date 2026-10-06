# Padrão de commit

| Tipo         | Descrição                                                                     | Exemplo                                                                                            |
| ------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **feat**     | Quando da adição de um recurso, uma *feature* (funcionalidade).               | `feat(KERNEL-{ID}): Implementação dos repositories usados nas operações com as tabelas de variações climáticas` |
| **fix**      | Correção de um bug.                                                           | `fix(KERNEL-{ID}): Correção do componente de seleção de município`                                              |
| **docs**     | Atualização de documentação.                                                  | `docs(KERNEL-{ID}): Inclusão de diagrama de modelo de BD para a aplicação`                                      |
| **style**    | Mudança de formatação, sem afetar o código.                                   | `style(KERNEL-{ID}): Ajuste de nomes de variáveis para o padrão camelCase`                                      |
| **refactor** | Refatoração do código, sem alterar funcionalidade.                            | `refactor(KERNEL-{ID}): Ajuste na estrutura do código para melhor legibilidade`                                 |
| **test**     | Adiciona ou modifica testes.                                                  | `test(KERNEL-{ID}): Criação de testes unitários para o módulo de autenticação`                                  |
| **chore**    | Atualizações menores que não impactam diretamente a funcionalidade do código. | `chore(KERNEL-{ID}): Atualização de dependências do projeto`                                                    |
| **ci**       | Alterações nos pipelines de Integração Contínua e Deploy Automático.          | `ci(KERNEL-{ID}): Ajuste no workflow de deploy para rodar migrations antes de iniciar a aplicação`              |