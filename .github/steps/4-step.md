## Etapa 4: Automatize as Revisões


As revisões personalizadas parecem estar funcionando muito bem, mas há um problema: elas não são tecnicamente obrigatórias. Solicitar revisões do Copilot manualmente não é sustentável quando há vários professores contribuindo para o site de atividades. Você quer que todo pull request receba automaticamente o feedback do Copilot, especialmente porque há diferentes níveis de experiência em programação entre os colaboradores. Vamos configurar regras do repositório para exigir revisões do Copilot em todas as mudanças.

### 📖 Teoria: Regras de Repositório para Revisões Automáticas


As regras do repositório permitem impor revisões automáticas de código em todos os pull requests, garantindo verificações de qualidade consistentes sem depender dos desenvolvedores para solicitar revisões manualmente ou lembrar de seguir a documentação.


Cada revisão de código consome uma [Unidade de Solicitação Premium (PRU)](https://docs.github.com/en/copilot/concepts/billing/copilot-requests) do autor do pull request.


**Opções de Aplicação:**


- **Nível de repositório**: Todos os novos pull requests no repositório específico
- **Nível de branch**: Direciona branches específicas por filtros e padrões de nome
- **Nível de organização**: Aplica regras em múltiplos repositórios


**Principais Benefícios:**


- Qualidade de código consistente em todas as contribuições
- Aplicação automática sem intervenção manual
- Configurável conforme as necessidades de proteção de branch
- Integração com as permissões do fluxo de trabalho do GitHub


Para mais informações, veja a [documentação de regras de repositório](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

### ⌨️ Atividade: Crie uma regra de repositório


1. No menu superior, selecione a aba **Settings**.


1. No menu à esquerda, expanda **Rules** e selecione **Rulesets**.


1. Clique no botão **New ruleset** e selecione a opção **New branch ruleset**.


1. Defina o nome e o status da regra:


   - **Ruleset Name**: `Require Copilot Reviews`
   - **Enforcement Status**: `Active`


1. Em **Target branches**, adicione proteções para a branch `main`.


   1. Clique em **Add target** e **Include default branch**.
   1. Clique em **Add target** e **Include by pattern**.
   1. Digite `main` e clique em **Add inclusion pattern**.

   <img width="300" alt="screenshot of target branches" src="https://github.com/user-attachments/assets/217f205c-7a61-4ffa-a0a6-7e76ff8d7906"/>


1. Em **Rules**, habilite as opções abaixo:


   - **Exigir pull request antes de mesclar**: ☑️
   - **Exigir resolução de conversas antes de mesclar**: ☑️
   - **Solicitar automaticamente revisão de código do Copilot**: ☑️


1. Role até o final e clique em **Create**.


1. Volte para o pull request aberto.


1. Note que o botão de merge agora está desabilitado.

   <img width="300" alt="screenshot of disabled merge button" src="https://github.com/user-attachments/assets/28e4cb05-f09d-423d-8c77-8f0ec61c73ad"/>


1. Clique em **Resolve conversation** para todo feedback atual e antigo do Copilot. Não é necessário implementar nada.


1. Faça o merge do pull request.


   > 🪧 **Nota**: Se o botão **Merge pull request** não ativar, verifique se há conversas não resolvidas nos comentários antigos.


1. Com o pull request mesclado, aguarde um momento para a Mona checar seu trabalho, fornecer feedback e fazer a revisão final. Parabéns! Você terminou! 🎉

### ⌨️ Atividade: (opcional) Teste revisões automáticas


Ainda não quer terminar? Está incomodado com o banner de anúncio hard coded? Nós também!


Então... vamos corrigir isso! 🧑‍🚀🚀


> [!NOTA]
> Você não precisa "corrigir" o novo recurso de Anúncio. Se quiser apenas testar as revisões automáticas, basta fazer uma pequena alteração e abrir um novo pull request.


1. No VS Code, volte para a branch `main`, puxe as alterações mescladas e exclua a branch `add-announcement-banner`.


1. Crie uma nova branch a partir da `main` com o nome abaixo.

   ```txt
   enable-editing-announcements
   ```


1. Abra o painel do Copilot Chat e certifique-se de que está no **modo Agent**. Use o prompt abaixo para pedir ao Copilot que melhore o novo recurso de Anúncios.


   > 💡 **Dica**: Os modelos premium (que usam PRUs) normalmente são mais robustos e exigem menos prompts de refinamento.


   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > O recurso de Anúncio não deve ser hard coded.
   >
   > - Faça com que seja alimentado pelo banco de dados.
   > - Adicione um botão no cabeçalho que abre uma janela de diálogo. Ela lista todos os anúncios existentes e tem controles para adicionar/modificar/excluir.
   > - Apenas usuários logados podem gerenciar anúncios.
   > - Anúncios exigem data de expiração. Data de início é opcional.
   > - Adicione uma mensagem de exemplo na inicialização do banco de dados.
   > - Não se preocupe com testes unitários.
   > - Capriche na experiência de UI/UX.
   > ```

1. (opcional) Rode a aplicação para testar as mudanças e forneça prompts adicionais ao Copilot para refinar ainda mais.

1. (opcional) Antes de fazer commit das mudanças, peça uma revisão local no VS Code.

1. Faça commit e push das alterações.

1. Crie um novo Pull Request com os seguintes detalhes.

   - **compare:** `enable-editing-announcements`
   - **target:** `main`
   - **title:** `Enable Editing Announcements`

1. Note que o Copilot foi adicionado automaticamente como revisor. Aguarde um momento pelo feedback.

1. (opcional) Resolva quaisquer comentários do Copilot.

1. Faça o merge do pull request.

1. Muito bom! Você terminou tudo, de novo! 🎉
