# Momento Data Insights 📊  

## 📂 **Departamento de Tecnologia**  
1️⃣ **Adicione suas informações ao departamento de Tecnologia da empresa.**  
```sql  
INSERT INTO funcionarios(funcionario_id, primeiro_nome, sobrenome, email, senha, telefone, data_contratacao, cargo_id, salario, gerente_id, departamento_id)  
VALUES (208, 'Emilly', 'Lourenço', 'mimi.emilly005@gmail.com', 'Mih788', '98792-4532', '2024-12-01', 20, 30.000, NULL, 6);  
```  

2️⃣ **Quantos funcionários temos ao total na empresa?**  
**Resposta:** São **42 funcionários** ao todo.  
```sql  
SELECT COUNT(*) FROM momento.funcionarios;  
```  

3️⃣ **Quantos funcionários trabalham no Departamento de Tecnologia?**  
**Resposta:** **6 funcionários** trabalham no Departamento de Tecnologia.  
```sql  
SELECT COUNT(*) FROM momento.funcionarios WHERE departamento_id = 6;  
```  

## 📂 **Departamento de Vendas**  
4️⃣ **Quantos funcionários trabalham no Departamento de Vendas?**  
**Resposta:** **5 funcionários** trabalham no Departamento de Vendas.  
```sql  
SELECT COUNT(*) FROM momento.funcionarios WHERE departamento_id = 8;  
```  

5️⃣ **Qual é o custo total dos salários do pessoal de Vendas?**  
**Resposta:** O custo total é de **R$51.500,00**.  
```sql  
SELECT SUM(salario) FROM momento.funcionarios WHERE departamento_id = 8;  
```  

6️⃣ **Quais produtos mais vendem e quais têm pouca ou nenhuma saída?**  
**Resposta:**  
- Produtos mais vendidos: *Uniforme do Superman* e *Capacete do Homem-Formiga*.  
- Pouca saída: *Laço da Honestidade* e *Batarangues Oficiais*.  
```sql  
SELECT produto_nome, quantidade  
FROM momento.vendas  
INNER JOIN produtos ON produtos.produto_id = vendas.produto_id  
ORDER BY quantidade DESC;  
```  

## 📂 **Departamento de Inovações**  
7️⃣ **Adicione o novo departamento de Inovações ao banco de dados:**  
```sql  
INSERT INTO escritorios(escritorio_id, escritorio_nome, endereco, cep, cidade, estado_provincia, pais_id)  
VALUES (2000, "Estúdio de Inovação", 'Senac Lapa Tito', '05051-000', 'São Paulo', 'São Paulo', 'BR');  

INSERT INTO departamentos(departamento_id, departamento_nome, escritorio_id)  
VALUES (14, 'Inovação', 2000);  
```  

8️⃣ **Inclua funcionários no departamento de Inovações:**  
```sql  
INSERT INTO funcionarios(funcionario_id, primeiro_nome, sobrenome, email, senha, telefone, data_contratacao, cargo_id, salario, gerente_id, departamento_id)  
VALUES (209, 'Vinicius', 'Cezario', 'vinascez@gmail.com', 'starwars20#@', '5421-4455', '2024-10-31', 20, 12000.00, NULL, 14),  
       (210, 'Gustavo', 'Gabriel', 'gugabriel@gmail.com', 'gatoflamingo55$', '5428-1475', '2024-10-31', 20, 12000.00, NULL, 14),  
       (211, 'Elton', 'Santos', 'eltonsantos@gmail.com', 'nba10#', '1421-7432', '2024-10-31', 20, 12000.00, NULL, 14);  
```  

## 📂 **Funcionários**  
9️⃣ **Quantos funcionários da empresa possuem cônjuges?**  
**Resposta:** **37 funcionários** possuem cônjuges.  
```sql  
SELECT COUNT(*) FROM momento.funcionarios  
INNER JOIN dependentes ON funcionarios.funcionario_id = dependentes.funcionario_id;  
```  

🔟 **Quem foi contratado há mais tempo?**  
**Resposta:** *Steven Wayne*, desde 1987.  
```sql  
SELECT CONCAT(primeiro_nome, " ", sobrenome) AS nome_funcionario, data_contratacao  
FROM momento.funcionarios  
ORDER BY data_contratacao;  
```  

## 📂 **Salários e Departamentos**  
1️⃣1️⃣ **Qual a média salarial dos funcionários da empresa Momento, excluindo o CEO, CMO e CFO?**  
**Resposta:** **R$8.496,67**.  
```sql  
SELECT AVG(salario) AS Media_Salarial  
FROM funcionarios  
WHERE cargo_id NOT IN (4, 7, 10);  
```  

1️⃣2️⃣ **Qual departamento possui a maior média salarial?**  
**Resposta:** *Departamento de Tecnologias Avançadas*, com **R$21.815,00**.  
```sql  
SELECT departamentos.departamento_nome, AVG(salario) AS Media_Salarial  
FROM funcionarios  
INNER JOIN departamentos ON departamentos.departamento_id = funcionarios.departamento_id  
GROUP BY departamento_id  
ORDER BY Media_Salarial DESC;  
```  
