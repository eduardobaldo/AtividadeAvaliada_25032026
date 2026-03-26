# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Eduardo Baldo
RA: 25001247 
Data: 25/03/2026

---

# 1. Definição do MVP
Meu MVP cobre o processo de venda a partir da identificação do cliente até a conclusão da venda, incluindo atualização automática de estoque, cancelamento de compra por estoque insuficiente.
Nele, contém funcionalidades como consulta de produtos e seus respectivos estoques, cadastro e verificação do cliente e controle de estoque.
Fora do MVP estão os métodos de controle completo de capital (contas a receber/a pagar), relatórios, integração de processos.
Esse MVP foi escolhido priorizando o funcionamento básico principal de uma farmácia, ou seja, as vendas e controle de estoque.

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 — Venda somente se estoque disponível** 
Um produto só poderá ser vendido se o estoque do mesmo foi maior que 0.

**RN02 — Restrição de funções por tipo de cadastro**
Algumas funções do sistema só poderão ser acessadas por usuários com tipo de cadastros específicos (como atendentes e gerentes, por exemplo).

**RN03 — Atuliação de estoque**
Toda venda deverá atualizar o estoque de acordo com os produtos que saíram.

**RN04 — Cancelamento em caso de estoque indisponível**
Caso a quantidade de um produto requisitada pelo cliente for maior que a quantidade disponível em estoque, a venda deverá ser cancelada, informando a quantidade disponível (se houver).

**RN05 — Registro de venda**  
Toda venda deve gerar um registro, para futuras consultas.

(Adicione mais se quiser.)

---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 — Realizar venda**  
O sistema deve ser capaz de realizar a venda de qualquer produto da farmacia

**RF02 — Atualização automática de estoque**  
A cada venda, o sistema deve atualizar automaticamente o estoque, deduzindo a quantidade vendida.

**RF03 — Alerta de nível baixo de estoque**  
Caso o estoque de algum produto atinja um percentual pré-definido, o sistema deve emitir um alerta.

**RF04 — Pesquisa de produtos**  
O sistema deve perimitir a consulta de produtos pelo nome, código, fabricante

**RF05 — Verificar disponibilidade**  
Durante a consulta, o sistema deve mostrar a disponibilidade do produto.

**RF06 — Cancelamento de compra em caso de estoque insuficiente**  
Caso um cliente tente comprar um produto cuja quantidade não atenda à requisitada, a venda deve ser cancelada.

**RF07 — Limitação de funções por tipo de usuário**  
Cada usuário terá um tipo de cadastro de acordo com a sua função, e algumas funções estarão limitadas a isso.

**RF08 — Cadastrar cliente**  
O sistema deve permitir o cadastro de clientes para armazenar histórico de compras ou realizar vendas à prazo.

(Adicione mais se quiser.)

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 — Desempenho**
As consultas de produtos no estoque deverão ser realizadas em até 3 segundos.

**RNF02 — Segurança**  
O acesso às funções e informações do sistema só se darão a um usuário autenticado.

**RNF03 — Disponibilidade**
Durante todo o expediente da farmácia, o sistema deve estar funcional.

**RNF04 — Usabilidade**
A interface do sistema deve permitir que as vendas sejam realizadas rapidamente, de forma intuitiva.

(Adicione mais se quiser.)

---

# 5. Casos de Uso (mínimo: 10)
**UC01 - Realizar venda**

**UC02 - Conferir estoque**

**UC03 - Cadastrar cliente**

**UC04 - Identificar cliente**

**UC05 - Atualizar estoque**

**UC06 - Enviar alerta de estoque baixo**

**UC07 - Cancelamento de venda em caso de estoque insuficiente**

**UC08 - Cadastrar usuário**

**UC09 - Autenticar usuário**

**UC10 - Registrar venda**

<img width="715" height="706" alt="Captura de tela 2026-03-25 211312" src="https://github.com/user-attachments/assets/99f59a15-c8ef-4630-8b8a-4381ac73ef17" />



---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UC01 — Realizar venda**
**Ator(es): Atendente**  
**Descrição: O sistema permite que o atendente realize a venda de um ou mais produtos, desde que o estoque permita.**  
**Pré-condições: Cliente identificado, produto em estoque**  
**Pós-condições: Venda realizada, estoque atualizado**  

### Fluxo Principal
1.  Atendente identifica (ou cadastra, se necessário) o cliente.
2.  Atendente escolhe os produtos e quantidade.
3.  O sistema verifica se a quantidade requisitada está disponível.
4.  Venda realizada.

### Fluxos Alternativos / Exceções
- FA01 —  Estoque insuficiente
  O sistema cancela a venda e informa a quantidade encontrada.
- FA02 —  Cliente não identificado
  O sistema avisa que o cliente não possui cadastro e realiza rapidamente.

### Relacionamentos
- **Include:** localizar cliente, conferir estoque, registrar venda
- **Extend:** cancelamento de venda em caso de estoque insuficiente, cadastrar cliente. 

<img width="418" height="633" alt="Captura de tela 2026-03-25 214222" src="https://github.com/user-attachments/assets/96f4e16a-c6d3-4a79-a473-d88eed7fb50e" />

---

## **UC02 — Conferir estoque**
**Ator(es):**  Atendente.
**Descrição:**  Informa a quantidade de itens encontrados no estoque, de acordo com a pesquisa.
**Pré-condições:**  Produto cadastrado, usuário autentcado.
**Pós-condições:**  Exibe a quantidade em estoque.

### Fluxo Principal
1.  Atendente pesquisa e seleciona o produto desejado.
2.  Sistema exibe a quantidade

### Fluxos Alternativos / Exceções
- FA01 —  Produto não cadastrado: sistema exibe mensagem de erro e inicia nova pesquisa.

### Relacionamentos
- **Include:**
- **Extend:**

<img width="518" height="403" alt="Captura de tela 2026-03-25 214304" src="https://github.com/user-attachments/assets/822aac4d-421a-42e2-a53e-ddd66a5c7497" />

---

## **UC03 — Cadastrar cliente**
**Ator(es):**  Atendente
**Descrição:**  O sistema permite cadastrar um cliente para registrar histórico de vendas
**Pré-condições:**  Usuário autenticado
**Pós-condições:**  Cliente cadastrado

### Fluxo Principal
1.  Atendente preenche os dados necessário para o cadastro
2.  Sistema registra o cliente

### Fluxos Alternativos / Exceções
- FA01 —  Cliente já cadastrado: exibe um aviso de que o cliente já possui cadastro.

### Relacionamentos
- **Include:** 
- **Extend:** identificar cliente

<img width="507" height="350" alt="image" src="https://github.com/user-attachments/assets/24816a7a-cbcf-4d20-b674-82f639c5bad7" />

---

## **UC04 — Identificar cliente**
**Ator(es):**  Atendente
**Descrição:**  Pesquisa nos cadastros um cliente em específico
**Pré-condições:**  Cliente cadastrado
**Pós-condições:**  Cliente identificado ou mensagem de erro

### Fluxo Principal
1.  Atendente pesquisa um cliente por nome ou algum dado.
2.  Sistema exibe o cliente e histórico de vendas.

### Fluxos Alternativos / Exceções
- FA01 —  Cliente não encontrado: Exibe mensagem de erro e dá a opção de acessar a tela de cadastro.

### Relacionamentos
- **Include:**   
- **Extend:** cadastrar cliente

<img width="539" height="350" alt="image" src="https://github.com/user-attachments/assets/55403c77-ff32-4e68-b71a-267b167c3d2c" />

---

## **UC05 — Atualizar estoque**
**Ator(es):**  Sistema
**Descrição:**  Atualiza automaticamente o estoque após uma venda
**Pré-condições:**  Venda realizada com sucesso
**Pós-condições:**  Estoque deduz a quantidade vendida

### Fluxo Principal
1.  Sistema executa uma venda
2.  Sistema atualiza estoque
3.  Caso seja detectada quantidade baixa de estoque, emite alerta

### Fluxos Alternativos / Exceções
- FA01 —  

### Relacionamentos
- **Include:** 
- **Extend:** enviar alerta de estoque baixo

<img width="288" height="434" alt="image" src="https://github.com/user-attachments/assets/bc5fa7d7-8acb-4593-a005-9c849b3162ac" />

---

## **UC06 — Enviar alerta de estoque baixo**
**Ator(es):**  Sistema
**Descrição:**  Envia alerta se a quantidade em estoque de um item for baixa
**Pré-condições:**  Estoque considerado baixo
**Pós-condições:**  Alerta enviado para o usuário

### Fluxo Principal
1.  Sistema identifica quantidade baixa de estoque
2.  Sistema envia um alerta.

### Fluxos Alternativos / Exceções
- FA01 —  Produto com estoque "seguro": Sistema não gera alerta.

### Relacionamentos
- **Include:** 
- **Extend:** atualizar estoque
  
<img width="440" height="350" alt="image" src="https://github.com/user-attachments/assets/528e3902-6461-401d-982b-20552fe942d1" />

---

## **UC07 — Cancelamento de venda em caso de estoque insuficiente**
**Ator(es):**  Sistema
**Descrição:**  Interrompe a venda se a quantidade requisitada não está disponível
**Pré-condições:**  Venda em andamento, produto com pouco estoque
**Pós-condições:**  Venda cancelada

### Fluxo Principal
1.  Sistema avalia estoque insuficiente para a venda
2.  Sistema cancela a compra e informa o atendente

### Fluxos Alternativos / Exceções

### Relacionamentos
- **Include:** 
- **Extend:** realizar venda

<img width="430" height="397" alt="image" src="https://github.com/user-attachments/assets/fa08f606-fa21-4d63-84f0-545037dd1613" />

---

## **UC08 — Cadastrar usuário**
**Ator(es):**  Gerente
**Descrição:**  Registra novos usuários (funcionários) da farmácia, com perfis divididos em tipos.
**Pré-condições:**  Usuário gerente autenticado
**Pós-condições:**  Novo usuário cadastrado

### Fluxo Principal
1.  Gerente informa os dados do usuário
2.  Sistema registra o cadastro

### Fluxos Alternativos / Exceções
- FA01 —  Usuário existente: gera um alerta e cancela a operação

### Relacionamentos
- **Include:** 
- **Extend:** 

<img width="408" height="350" alt="image" src="https://github.com/user-attachments/assets/5f3fa631-2f42-4f50-93a9-fe8d790183ec" />

---

## **UC09 — Autenticar usuário**
**Ator(es):**  Sistema
**Descrição:**  Permite que um usuário faça login e utilize as funções correspondentes
**Pré-condições:**  Usuário cadastrado
**Pós-condições:**  Usuário autenticado

### Fluxo Principal
1.  Usuário informa login e senha
2.  Sistema valida e autentica o usuário

### Fluxos Alternativos / Exceções
- FA01 —  Dados inválidos: cancela a autenticação e dá nova tentativa de login
- FA02 —  Muitas tentativas: se o usuário errar 5 vezes, bloqueia o acesso

### Relacionamentos
- **Include:**
- **Extend:**

<img width="560" height="486" alt="image" src="https://github.com/user-attachments/assets/d2c1293e-b632-495a-b964-4e79d9e501ad" />

---

## **UC10 — Registrar venda**
**Ator(es):**  Sistema
**Descrição:**  Registra a venda atrelada ao cadastro do cliente
**Pré-condições:**  Venda realizada
**Pós-condições:**  Venda registrada no banco de dados

### Fluxo Principal
1.  Sistema conclui uma venda
2.  Sistema armazena as informações arealadas ao cliente

### Fluxos Alternativos / Exceções

### Relacionamentos
- **Include:**
- **Extend:**

<img width="277" height="341" alt="image" src="https://github.com/user-attachments/assets/6cc52e08-2dde-4b23-97e9-98829ef09c34" />

---
