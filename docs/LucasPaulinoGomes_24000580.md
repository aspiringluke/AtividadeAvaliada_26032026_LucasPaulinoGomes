# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Lucas Paulino Gomes
RA: 24000580
Data: 26/03/2026

---

# 1. Definição do MVP

O MVP consiste em três partes principais para o funcionamento básico do software:
- Compras e vendas, incluindo o processo do início até o registro/checkout
- Gestão de estoque, intimamente ligado às vendas para controlar a quantidade de cada produto
- Financeiro, para registrar tanto as contas a pagar quanto a receber, à vista e a prazo

Haverá tratamento de erros básico no sistema. Todo o resto estará fora, pois não é estritamente
necessário para o funcionamento.

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 — Limite pela quantidade em estoque**
Cada venda só poderá ser realizada se houver quantidade suficiente do produto
requisitado em estoque

**RN02 — Cadastro de produto**
Um novo produto só deve ser cadastrado se tiver todas as informações requisitadas

**RN03 — Produto esgotado**
Produtos fora do estoque não podem ser vendidos

**RN04 — Histórico do cliente**
Devoluções deverão ser registradas no histórico do cliente

**RN05 — Cancelamento de venda**
Uma venda só poderá ser cancelada se
1. o produto não tiver sido utilizado, e
2. a devolução for realizada dentro de 15 dias

---

# 3. Requisitos Funcionais (mínimo: 8)

**RF01 — Registrar venda**
Registro de venda realizadas no balcão ou por telefone, podendo ser
à vista (pagamento imediato) ou a prazo (pagamento parcelado ou postergado)

**RF02 — Atualizar estoque**
Atualização automática das quantidades em estoque após qualquer uma dessas
operações:
- venda
- devolução
- perda
- transferência
- reposição após compra

**RF03 — Cadastrar produto**
Cadastro de novo produto com descrição, preço de venda, unidade de medida e fabricante

**RF04 — Registrar cliente**
Registro de cliente no banco de dados da farmácia com nome e CPF/CNPJ

**RF05 — Vincular produto ao cliente**
Cada nova venda pode ser vinculada a um cliente caso ele esteja registrado no sistema

**RF06 — Notificar vencimento de conta**
O sistema deve enviar uma notificação ao gerente quando uma conta (a pagar ou a receber)
estiver a 1 semana de vencer, e outra quando estiver vencida

**RF07 — Atualizar conta a pagar/receber**
Quando uma conta vencer ou for paga, o sistema deve ajustar o status para o valor correspondente

**RF08 — Cancelar venda**
Numa devolução, a venda pode ser cancelada

**RF09 — Emitir comprovante**
O sistema deve emitir um comprovante a cada venda realizada

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 — (Eficiência de Desempenho) Tempo de resposta**
O sistema dever responder a solicitações simples em menos de 30ms

**RNF02 — (Segurança) Operações financeiras**
Todas as operações financeiras devem ser autenticadas com tokens e registradas para auditoria

**RNF03 — (Interoperabilidade) Padrão de comunicação**
O sistema deve utilizar padrões REST para comunicação em rede, a fim de facilitar
a integração entre diferentes unidades da empresa

**RNF04 — (Manutenibilidade) Estrutura do código**
A aplicação deve ser modular e apresentar baixo acoplamento entre módulos e classes

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- pelo menos 3 includes
- pelo menos 3 extends

---

# 6. Documentação dos Casos de Uso

## **UC01 — Registrar venda à vista**
**Ator(es): Atendente, sistema**
**Descrição: Registra a venda de um medicamento**
**Pré-condições: Nenhuma**
**Pós-condições: Venda registrada e estoque atualizado**

### Fluxo Principal
1. Atendente pesquisa um produto no sistema
2. Sistema procura e retorna os resultados correspondentes
3. Atendente seleciona o produto desejado
4. Atendente insere a quantidade
5. Sistema valida a quantidade
6. Atendente marca a venda como à vista
7. Sistema registra a venda no banco e retorna sucesso
8. Sistema emite comprovante

### Fluxos Alternativos / Exceções
- FA01 — Produto não encontrado
1. Sistema retorna mensagem de "não encontrado"
- FA02 — Estoque insuficiente
1. Sistema percebe que a quantidade solicitada excede a em estoque
2. Sistema retorna mensagem de erro
- FA03 — Registro de venda a prazo
Ver UC02

### Relacionamentos
Nenhum

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC02 — Registrar venda a prazo**
**Ator(es): Atendente, sistema**
**Descrição: Registrar vendas de medicamentos a prazo**
**Pré-condições: Nenhuma**
**Pós-condições: Venda a prazo adicionada às contas a receber**

### Fluxo Principal
1. Atendente inicia o registro da venda
2. Atendente marca a venda como a prazo
3. Sistema adiciona a venda às contas a receber
4. Sistema retorna mensagem de sucesso
5. Sistema emite comprovante

### Fluxos Alternativos / Exceções
Nenhum aparente

### Relacionamentos 
- **Extend:** UC01

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC03 — Registrar cliente**
**Ator(es): Atendente, sistema**
**Descrição: Registro de cliente para acompanhamento do histórico de compra**
**Pré-condições: Nenhuma**
**Pós-condições: Cliente registrado no banco de dados da empresa**

### Fluxo Principal
1. Atendente abre a página de registro de cliente
2. Atendente insere as informações do cliente
3. Sistema verifica a existência do cliente no banco
4. Sistema cadastra o cliente no banco
5. Sistema retorna mensagem de sucesso

### Fluxos Alternativos / Exceções
- FA01 — Dados insuficientes
1. O atendente tenta cadastrar sem algum dos dados necessários
2. Sistema identifica o erro e retorna um aviso
- FA02 — Cliente existente
1. Sistema encontra um cliente com os mesmos dados no banco
2. Sistema retorna um aviso e os dados

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC04 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC05 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC06 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC07 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC08 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC09 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

## **UC10 — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---
