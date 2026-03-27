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

**RN01 —**  
**RN02 —**  
**RN03 —**  
**RN04 —**  
**RN05 —**  

(Adicione mais se quiser.)

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

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —**  
**RNF02 —**  
**RNF03 —**  
**RNF04 —**  

(Adicione mais se quiser.)

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 10 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UCXX — Nome do Caso de Uso**
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

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).


