Desafio de Projeto – Integração do Power BI com o MYSQL.

IMPORTANTE:

	Devido ao fato de eu não possuir cartão de crédito para poder criar um conta o Azure, criei o desafio usando o MYSQL instalado localmente.
DESAFIO E RESOLUÇÃO 
Durante a execução dos Scripts , me deparei com o seguinte erro ao inserir os dados:
Error Code: 1452. Cannot add or update a child row: a foreign key constraint fails (`azure_company`.`employee`, CONSTRAINT `fk_employee` FOREIGN KEY (`Super_ssn`) REFERENCES `employee` (`Ssn`) ON DELETE SET NULL ON UPDATE CASCADE)	0.016 sec
A solução encontrada foi desabilitar a verificação de chave estrengeira para possibilitar a inserção dos dados usando o comando : 
	SET foreign_key_checks = 0;
Após a inserção, foi necessário reabilitar a verificação das FK's.

CONECTANDO AO BANCO DE DADOS

Para que o Power BI conseguisse se conectar ao MYSQL foi preciso instalar o MYSQL Connector
Após a conexão com o Banco de dados foi necessário transformar os dados
Divisão do endereço (item 8):
Para evitar o erro na divisão do endereço devido ao bairro de Fire-Oak(Huble), a divisão foi feita em etapas
Isolei o número, usando a opção de considerar apenas o primeiro delimitador
Isolei o estado usado a opção de considerar o último delimitador
Isolei a cidade usando a opção de considerar o último delimitador
Por fim, as colunas foram renomeadas

ITEM 11:
A junção das dos colaboradores com seus gerentes foi feita usando como chave a matricula do gerente no departamento com o SSN na tabela Employee

A mesclagem do nome foi feita a partir da opção "Mesclar colunas" da Guia Adicionar Colunas

ITEM 14:
o mesclar foi utilizado pois o objetivo é a criação de uma nova coluna de valores e não a criação de uma consultas com valores com a criação de dados de outras tabelas


QUALIDADE DOS DADOS: 

![image](https://github.com/andresantana1988/desafio_power_bi_mysql/assets/100046339/eb5b75dc-741d-44ae-8419-67176b9c19b0)

