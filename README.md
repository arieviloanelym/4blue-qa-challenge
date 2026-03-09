**Teste Técnico – QA Tester - 4blue**

**1. Identificação de Bugs**

**Bug 01:** Cadastro e Login com campos obrigatórios vazios

Título: Permissão de criação de conta e autenticação sem preenchimento de dados.

Descrição: O sistema não valida se os campos estão vazios, permitindo que o usuário crie uma conta nula e acesse o sistema sem e-mail e senha.

Passos para reproduzir:

1 - Acessar o link https://qa-play-sim.lovable.app/ 

2 - Clicar em "Criar conta" 

3 - Clicar no botão "Criar conta" sem preencher nenhum campo

4 - Voltar para a tela de Login

5 - Clicar em "Entrar" sem preencher nenhum campo

(Gif)
![chrome_3KyeU5FPan](https://github.com/user-attachments/assets/b19ad155-53b7-4ccc-848d-5fcdc45b9f6c)

Resultado atual: O sistema exibe mensagem de sucesso e permite o acesso.

Resultado esperado: O sistema deve impedir o avanço e exibir a mensagem "Campo obrigatório" em cada campo vazio.

Severidade: Crítico

Prioridade: Alta

--

**Bug 02:** Exposição de credenciais no Console do navegador

Título: Exposição de senha em texto claro nos logs do Console (DevTools).

Descrição: Ao submeter os formulários de login ou cadastro, o e-mail e a senha digitada é impressa abertamente no console do desenvolvedor.

Passos para reproduzir:

1 - Abrir o Inspecionar do navegador (F12) e clicar na aba "Console"

2 - Realizar uma tentativa de cadastro ou login preenchendo o campo de e-mail e senha

Cadastro
<img width="1920" height="912" alt="image" src="https://github.com/user-attachments/assets/926dea74-0088-4aa0-929c-d32e91fb95e6" />

Login
<img width="1920" height="912" alt="image" src="https://github.com/user-attachments/assets/f097080e-0247-453e-87ef-2961cd2cda36" />

Resultado atual: A senha aparece escrita em texto claro no log do console.

Resultado esperado: Informações sensíveis (senhas) não devem ser registradas em logs por questões de segurança e privacidade.

Severidade: Crítico

Prioridade: Alta

--

**Bug 03:** Falha na validação de requisitos de senha

Título: Aceitação de senhas que não cumprem os requisitos de segurança informados.

Descrição: O sistema informa que a senha precisa de 8 caracteres e 1 especial, mas permite o cadastro com apenas o número "1".

Passos para reproduzir:

1 - Acessar o link https://qa-play-sim.lovable.app/ 

2 - Clicar em "Criar conta"

3 - No campo senha, digitar apenas "1"

4 - Clicar em "Criar conta"

(Gif)
![chrome_bAiXAz1G9D](https://github.com/user-attachments/assets/7be5595f-f89d-4d58-a4e4-002aa388c2ee)

Resultado atual: A conta é criada com sucesso mesmo com senha insegura.

Resultado esperado: O sistema deve validar a senha e exibir erro caso os requisitos não sejam atingidos.

Severidade: Alto

Prioridade: Alta

--

**Bug 04:** Estouro de Layout

Título: Campos de input extrapolando o limite lateral do modal.

Descrição: Na tela de cadastro, os campos "Telefone" e "Confirmar Senha" não respeitam as margens do container principal, ultrapassando visualmente a borda do modal branco. E os campos "Nome" e "Senha" estão atras dos campos "Telefone" e "Confirmar Senha".

Passos para reproduzir:

1 - Acessar o link https://qa-play-sim.lovable.app/ 

2 - Clicar em "Criar conta" 

3 - Observar o alinhamento dos campos no lado direito do formulário

<img width="1920" height="912" alt="image" src="https://github.com/user-attachments/assets/f1abae78-9197-41d4-bfca-ec3e32a7f4b7" />

Resultado atual: Os inputs de "Telefone" e "Confirmar Senha" estão maiores que o modal, vazando para fora da área branca e os campos de "Nome" e "Senha" estão atrás dos campos "Telefone" e "Confirmar Senha".

Resultado esperado: Todos os campos devem possuir um padrão e estar contidos dentro dos limites do modal, mantendo o alinhamento e o preenchimento (padding) uniforme.

Severidade: Baixo

Prioridade: Média

--

**Bug 05:** Falha de Responsividade (Mobile)

Título: Ausência de responsividade nas telas de Login e Cadastro.

Descrição: O sistema não possui adaptação para dispositivos móveis. 

Passos para reproduzir:

1 - Acessar o link https://qa-play-sim.lovable.app/ 

2 - Clicar em "Criar conta" 

3 - Ativar o DevTools ou acessar o link via mobile

(Gif)
![chrome_FCtPxjEgsC](https://github.com/user-attachments/assets/fff30afd-72eb-4ff7-94e4-c70f45c2a4e0)

Resultado atual: Impossibilidade de visualizar as telas corretamente.

Resultado esperado: O layout deve ser fluido e o sistema deve se adaptar sendo mobile ou desktop. 

Severidade: Médio

Prioridade: Alta

--

**2. Respostas do Teste**

Quais 2 bugs você corrigiria primeiro e por quê?

**Bug 01:** Cadastro e Login com campos obrigatórios vazios: Por ser uma falha funcional crítica que permite a entrada de dados nulos e compromete todo o funcionamento do sistema.

**Bug 02:** Exposição de credenciais no Console do navegador: Por ser uma falha de segurança grave que expõe dados sensíveis do usuário, o que é contra as boas práticas de segurança e LGPD.

**Sugestões de melhorias:**

**Bug 01**
Trava no Botão de Cadastro: Para evitar que o usuário envie o formulário vazio, o botão "Criar conta" deve começar desabilitado. Ele só deve ser liberado para clicar quando todos os campos marcados com o sinal de obrigatório (!) estiverem preenchidos.

Mensagens de Alerta: Além de desabilitar o botão, o sistema deve mostrar um aviso visual (como uma frase em vermelho ou o símbolo de exclamação) logo abaixo do campo que o usuário esqueceu de preencher, para ele saber exatamente o que falta fazer.

**Bug 02**
Proteção de Dados no Console: É necessário aplicar uma "máscara" ou bloqueio no código para que nenhuma informação digitada pelo usuário (como e-mail e senha) seja mostrada na tela de inspeção (Console). O sistema deve processar os dados de forma privada, garantindo que ninguém consiga visualizar o que foi escrito através das ferramentas de desenvolvedor.

-- 

**4. Sugestões de Ajustes Rápidos**

Além das correções críticas, listei alguns ajustes que podem melhorar muito a experiência de quem usa o sistema:

Padronização de Termos: Atualmente, o sistema usa as palavras "Plataforma" na tela de cadastro e "Sistema" na tela de login. A sugestão é escolher apenas um nome e usar em todas as mensagens para não confundir o usuário.

Correção do Botão de Sucesso: Assim que o usuário termina o cadastro, o botão aparece como "Sair da conta". O ideal é trocar o texto para "Acessar Sistema" ou "Ir para o Início".

Mensagem de Erro no Login: Quando o login falha, em vez de mostrar "Conta não encontrada", mudar para "E-mail ou Senha incorretos". 

