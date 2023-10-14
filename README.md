# banco-de-dados2

Desenvolva um banco de dados e relacione tabelas através de chaves estrangeiras ou nomes de colunas iguais. Siga as instruções:

crie uma base de dados; 
crie tabelas nessa base de dados;
em cada tabela, adicione atributos;
insira dados em cada tabela;
utilize os comandos Joins para realizar consultas nas tabelas.
<br>
<br>

create database biblioteca;
<br>
<br>
use database biblioteca;
<br>
<br>
create table autores (
    autorID serial primary key,
    nome varchar(100),
    nacionalidade varchar(50)
);
<br>
<br>
create table livros (
    livroID serial primary key,
    titulo varchar(255),
    autorID int references autores(autorID),
    anoPublicacao INT
);
<br>
<br>
create table emprestimos (
    emprestimoID serial primary key,
    livroID int references livros(livroID),
    usuario varchar(100),
    dataEmprestimo DATE,
    dataDevolucao DATE
);
<br>
<br>
insert into autores
    (nome, nacionalidade)
values
    ('J.K. Rowling', 'Britânica'),
    ('George Orwell', 'Britânica');
<br>
<br>
insert into livros
    (Titulo, autorID, anoPublicacao)
values
    ('Harry Potter e a Pedra Filosofal', 1, 1997),
    ('1984', 2, 1949);
<br>
<br>

insert into emprestimos
    (livroID, usuario, dataEmprestimo, dataDevolucao)
values
    (1, 'Alice', '2023-01-15', '2023-01-22'),
    (2, 'Bob', '2023-02-10', '2023-02-17');
<br>
<br>
select e.emprestimoID, l.titulo, a.nome, e.usuario
from emprestimos e
join livros l on e.livroID = l.livroID
join autores a on l.autorID = a.autorID;
<br>
<br>
Nesta consulta, joins (inner join) foram utilizados para combinar dados de três tabelas diferentes (emprestimos, livros e autores) com base nas chaves estrangeiras (livroID e autorID), obtendo informações sobre os empréstimos, títulos dos livros e nomes dos autores relacionados.
