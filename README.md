# locacaoautomoveisGV2

Atividade a seguir, possui objetivo de utilizar a forma de Normalização. A normalização é um processo no projeto de banco de dados que visa organizar as tabelas
de um banco de dados relacional de forma eficiente, minimizando a redundância de dados e
garantindo a integridade das informações. 

# 1º Observe a tabela não normalizada de uma locadora de veículos e aplique a 3ª Forma normal;
![image](https://github.com/huankzera/locacaoautomoveisGV2/assets/126423433/7d8e11af-03c4-4f23-acbf-1eb29580b7ac)


# 2º Faça o modelo lógico de banco de dados relacional;
![image](https://github.com/huankzera/locacaoautomoveisGV2/assets/126423433/cc7af655-2364-4a86-8518-500f933502c7)


# 3º Escreva o script que cria as tabelas;
``` SQL

create table Veiculos(
CarrosID int auto_increment primary key, 
Veiculo varchar(100),
Cor varchar(50),
Placa varchar(50),
Diaria decimal(15,9)
);

create table Cliente(
ClienteID int auto_increment primary key, 
Nome varchar(50),
CPF varchar(20),
Nascimento date
);

create table Locacao(
Cod_Locacao int primary key, 
Dias int(11), 

cliente_id int references Cliente(ClienteID),
carros_id int references Veiculos(CarrosID)
);
``` 

# 4º Crie uma view que seleciona todas as locações e seus respectivos veículos e clientes.
``` SQL
CREATE VIEW VeiculosLocados AS
SELECT L.Cod_Locacao, L.Dias, L.Total, 
       V.Veiculo, V.Cor, V.Placa, V.Diaria,
       C.Nome, C.CPF, C.Nascimento
FROM Locacao L
JOIN Veiculos V ON L.carros_id = V.CarrosID
JOIN Cliente C ON L.cliente_id = C.ClienteID;

select * from VeiculosLocados;
```
![image](https://github.com/huankzera/locacaoautomoveisGV2/assets/126423433/9193416d-737b-44d4-80a0-62951f9c8555)


Bancos de Ddaos 
