# MySQL Stored Procedures – Advanced Booking Automation

Este repositório contém um conjunto de **Stored Procedures avançadas em MySQL**, desenvolvidas para automatizar o processo de criação de aluguéis em lote, utilizando:

- Procedures encadeadas
- Tabelas temporárias
- Cursores
- Laços (`LOOP`)
- Tratamento de erros
- Manipulação de datas
- Regras de negócio no banco de dados

O projeto faz parte do estudo prático da base **InsightPlaces**, simulando um sistema de reservas/hospedagens.

---

## 🚀 Destaque Principal

A procedure **`novosAlugueis_55`** permite criar **vários aluguéis automaticamente** a partir de uma **lista de nomes de clientes**, processando cada cliente individualmente via cursor.

---

## 🧠 Lógica Geral da `novosAlugueis_55`

1. Recebe uma lista de nomes separados por vírgula  
2. Divide a lista e armazena os nomes em uma tabela temporária  
3. Percorre os nomes com um cursor  
4. Para cada cliente:
   - Calcula a data final (ignorando fins de semana)
   - Calcula o preço total
   - Gera um novo aluguel automaticamente
5. Executa validações e tratamento de erros durante o processo

---

## 📌 Procedure Principal

### `novosAlugueis_55`

```sql
CREATE PROCEDURE novosAlugueis_55(
    lista VARCHAR(255),
    vHospedagem VARCHAR(10),
    vDataInicio DATE,
    vDias INTEGER,
    vPrecoUnitario DECIMAL(10,2)
)
