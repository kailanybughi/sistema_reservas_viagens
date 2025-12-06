# 🛩 sistema_reservas_viagens
Projeto Final de Banco de Dados – Sistema de Reservas de Viagens.
# Sistema de Reservas de Viagens – Viajou Fácil

Este repositório contém a documentação completa do projeto de Banco de Dados para o sistema de reservas de viagens da agência online **Viajou Fácil**.

---

# 1. Cenário

## 1.1 Descrição da Empresa

A **Viajou Fácil** é uma agência online especializada em reservas de passagens aéreas, hospedagens e pacotes turísticos completos. Seu público-alvo inclui viajantes individuais, famílias e pequenas empresas que demandam agilidade, transparência e centralização na organização de suas viagens.

A plataforma permite ao usuário:

* Pesquisar destinos e pacotes disponíveis;
* Visualizar hotéis e serviços relacionados;
* Realizar reservas de viagens completas;
* Efetuar e acompanhar pagamentos;
* Registrar dados pessoais, contatos e endereços.

## 1.2 O Problema

Antes do sistema, o controle era feito de forma **manual**, utilizando planilhas e aplicações isoladas. Isso gerava problemas como:

* **Erros de digitação** e dados duplicados;
* **Falta de controle** sobre reservas ativas e destinos disponíveis;
* **Atraso na confirmação de pagamentos**;
* **Dificuldade para integrar informações** entre clientes, reservas e viagens;
* **Ausência de relatórios consolidados** para estratégia e gestão.

## 1.3 A Necessidade

O sistema foi criado para centralizar informações e automatizar processos, garantindo:

* Confiabilidade dos dados;
* Facilidade de manutenção e consultas;
* Padronização do fluxo de reservas;
* Melhor experiência do usuário;
* Operações rápidas e integradas entre clientes, viagens, reservas, hotéis e pagamentos.

---

# 2. Modelagem Conceitual

## Entidades e Atributos

CLIENTE
•	id_cliente (PK)
•	nome_cliente
•	email_cliente
•	telefone_cliente (multivalorado)
•	data_nascimento_cliente
ENDERECO_CLIENTE
•	id_endereco (PK)
•	id_cliente (FK)
•	rua
•	bairro
•	número
HOTEL
•	id_hotel (PK)
•	nome_hotel
•	categoria_hotel
•	preco_diaria_hotel
VIAGEM
•	id_viagem (PK)
•	id_hotel (FK)
•	nome_viagem
•	data_inicio_viagem
•	data_fim_viagem
•	descrição_viagem
•	preco_base_viagem
RESERVA
•	id_reserva (PK)
•	id_cliente (FK)
•	status_reserva
•	data_reserva
•	valor_total_reserva
PAGAMENTO
•	id_pagamento (PK)
•	id_reserva (FK)
•	metodo_pagamento
•	valor_pagamento
•	data_pagamento
•	status_pagamento

________________________________________

---

# Relacionamentos e Cardinalidades

| Nº | Entidade A | Entidade B       | Card. | Descrição                                      |
| -- | ---------- | ---------------- | ----- | ---------------------------------------------- |
| 1  | CLIENTE    | ENDERECO_CLIENTE | 1 : N | Um cliente pode ter múltiplos endereços        |
| 2  | CLIENTE    | VIAGEM           | 1 : N | Um cliente pode realizar várias viagens        |
| 3  | HOTEL      | VIAGEM           | 1 : N | Um hotel pode estar associado a várias viagens |
| 4  | DESTINO    | VIAGEM           | 1 : N | Um destino pode aparecer em várias viagens     |
| 5  | VIAGEM     | RESERVA          | 1 : 1 | Cada viagem possui uma única reserva           |
| 6  | RESERVA    | PAGAMENTO        | 1 : N | Uma reserva pode ter vários pagamentos         |

---

3. Modelagem Conceitual

A modelagem conceitual representa as entidades do sistema, seus atributos e os relacionamentos existentes entre elas.
A seguir estão as entidades identificadas no projeto e seus respectivos atributos:

📌 CLIENTE

id_cliente (PK)

nome_cliente

email_cliente

telefone_cliente (atributo multivalorado — um cliente pode ter vários telefones)

data_nascimento_cliente

📌 ENDERECO_CLIENTE

id_endereco (PK)

id_cliente (FK → CLIENTE.id_cliente)

rua

bairro

numero

📌 HOTEL

id_hotel (PK)

nome_hotel

categoria_hotel (antes chamada classificação, agora ajustado)

preco_diaria_hotel

📌 VIAGEM

id_viagem (PK)

id_hotel (FK → HOTEL.id_hotel)

nome_viagem

data_inicio_viagem

data_fim_viagem

descricao_viagem

preco_base_viagem

📌 RESERVA

id_reserva (PK)

id_cliente (FK → CLIENTE.id_cliente)

status_reserva

data_reserva

valor_total_reserva

📌 PAGAMENTO

id_pagamento (PK)

id_reserva (FK → RESERVA.id_reserva)

metodo_pagamento

valor_pagamento

data_pagamento

status_pagamento
---

# 4. Modelagem Física

Inclui:

* **Criação do banco de dados**;
* **Criação das tabelas** com tipos de dados e constraints;
* **Aplicação de chaves primárias e estrangeiras**;
* **Definição de relacionamentos** entre todas as entidades;
* **Restrições UNIQUE e CHECK**, quando aplicável.

Essa etapa transforma o modelo lógico em comandos SQL executáveis.

---

# 5. Dados

O sistema armazena informações como:

* Cadastro completo de clientes, telefones e endereços;
* Lista de hotéis e destinos internacionais e nacionais;
* Registro de viagens e status das reservas;
* Histórico de pagamentos e formas utilizadas;
* Preços totais e datas importantes para controle.

---

# 6. CRUD

## CREATE

Inserção de clientes, endereços, hotéis, destinos, viagens, reservas e pagamentos.

## READ

Consultas para:

* Listar viagens por cliente;
* Consultar reservas ativas;
* Exibir pagamentos pendentes;
* Listar destinos mais reservados.

## UPDATE

Atualizar dados como:

* Status da reserva;
* Pagamentos confirmados;
* Alteração de endereço ou telefone.

## DELETE

Remoção de registros respeitando integridade referencial. Ex.: não apagar hotel vinculado a viagem.

---

## 7. Relatórios

O sistema gera diversos relatórios úteis, como:

* 10 clientes mais recentes cadastrados

* Reservas com status pendente

* Viagens exibidas com seus respectivos hotéis

* Clientes listados com seus endereços

* Reservas associadas às suas viagens

* Hotéis com as diárias mais caras

* Viagens que começam após uma data específica

* Quantidade de reservas realizadas por cliente

* Quantidade de clientes por bairro

* Total gasto por cada cliente (soma das reservas)
