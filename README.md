# PDO4You

PDO é uma extensão do PHP, que permite aos desenvolvedores criar um código portável, de modo a atender a maioria dos bancos de dados mais populares. 
Sendo o MySQL, PostgreSQL, Oracle, SQLite.


Vantagens no uso da classe PDO4You:
==========
* Abstração de conexão
* Proteção contra SQL Injection
* Instrução SQL compacta



Verificando os drivers PDO suportados
-------------------------------------
Para verificar se o seu servidor tem suporte a um driver PDO de seu banco de dados, execute o seguinte método.

~~~ php
<<<<<<< HEAD
<?php

// O método getAvailableDrivers(), lista os drivers disponíveis que podem ser usados pelo DSN do PDO
foreach(PDO::getAvailableDrivers() AS $driver):
	echo $driver.'<br />';
endforeach;

?>
=======
	<?php

	// O método getAvailableDrivers(), lista os drivers disponíveis que podem ser usados pelo DSN do PDO
	foreach(PDO::getAvailableDrivers() AS $driver):
	    echo $driver.'<br />';
	endforeach;

	?>
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
~~~

O PDO provê uma camada abstrata de acesso a dados, que independentemente de qual banco de dados você esteja usando, você poderá usar as mesmas funções para emitir consultas e buscar dados.



O padrão de projeto Singleton otimiza a conexão, garantido uma única instância do objeto de conexão.

Carregando a interface
----------------------
<<<<<<< HEAD

~~~ php
<?php

// Carregando a interface
require '_inc/PDOConfig.class.php';
require '_inc/PDO4You.class.php';

?>
~~~ 

`PDOConfig.class.php`: contém os dados de conexão e uma biblioteca de funções relevantes.

=======

~~~ php
	<?php
	
	// Carregando a interface
	require '_inc/PDOConfig.class.php';
	require '_inc/PDO4You.class.php';
	
	?>
~~~ 

`PDOConfig.class.php`: contém os dados de conexão e uma biblioteca de funções relevantes.

>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
`PDO4You.class.php`: é a classe de conexão singleton PDO4You, baseada na extensão PDO.


DSN ou Data Source Name, contém as informações necessárias para se conectar ao banco de dados.



Conectando ao banco de dados via DSN (OPCIONAL). 
------------------------------------------------

~~~ php
<<<<<<< HEAD
<?php
=======
	<?php
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33

// Conexão direta via driver DSN
PDO4You::singleton('mysql:host=localhost;port=3306;dbname=pdo4you', 'root', '1234');

<<<<<<< HEAD
?>
=======
	?>
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
~~~ 



Abaixo segue um exemplo de como selecionar os registros no banco de dados, e em seguida como realizar o CRUD.

~~~ php
<<<<<<< HEAD
<?php
=======
	<?php
	
	// Conexão não-persistente
	PDO4You::singleton('mysql:host=localhost;port=3306;dbname=pdo4you', 'root', '1234',
		array(
			PDO :: ATTR_PERSISTENT => false 
		)
	);
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33

// Conexão não-persistente
PDO4You::singleton('mysql:host=localhost;port=3306;dbname=pdo4you', 'root', '1234',
	array(
		PDO :: ATTR_PERSISTENT => false 
	)
);


// Instânciando a conexão
$pdo = PDO4You::getInstance();

try {
	$sql = '
		SELECT
			u.* 
		FROM
			users u
	';
	$pre = $pdo->prepare($sql);
	$pre->execute();
	$dba_records = $pre->fetchAll(PDO::FETCH_ASSOC);
	$has_records = $pre->rowCount();
} catch (PDOException $e) {
	echo 'Error: '.$e->getMessage().'<br /><br />';
}

// Encerrando a conexão
$pdo = null;


// Imprimindo o total de registros
echo ' Total: '.$has_records.'<br />';


// Percorrendo o vetor com foreach e imprimindo os dados
foreach($dba_records as $dba):
	echo 'Nome: '.$dba["name"].'<br />';
enforeach;


<<<<<<< HEAD
// Outra forma de exibir os dados
echo ' Nome: '.$dba_records[0]["name"].'<br />';
echo ' Nome: '.$dba_records[1]["name"].'<br />';

?>
=======
	?>
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
~~~ 


O termo CRUD em inglês se refere as 4 operações básicas do banco de dados e significam: 
Create(INSERT), Retrieve(SELECT), Update(UPDATE) e Destroy(DELETE)


Os métodos "insert" , "update" e "delete" estão dentro das chamadas beginTransaction() e commit(), garantindo que ninguém veja as mudanças até que sejam concluídas. 
Se algo der errado, o bloco catch reverte todas as alterações feitas desde o início da transação e em seguida, imprime uma mensagem de erro.



Inserindo um registro no banco de dados
-----------------------------------------
~~~ php
<<<<<<< HEAD
// Exemplo de um INSERT
PDO4You::insert( 'users', 
	array(
=======
	// Exemplo de um INSERT
	PDO4You::insert( 'users', 
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
		array(
			'name'		=> $_POST["name"],
			'lastname'	=> $_POST["lastname"],
			'mail'		=> $_POST["mail"],
			'status'	=> 1
		)
<<<<<<< HEAD
	)
);
=======
	);
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
~~~ 


Atualizando os dados
--------------------
~~~ php
<<<<<<< HEAD
// Exemplo de um UPDATE
PDO4You::update( 'users', 
	array( array(
		array(
			'id' 		=> $_POST["id"]
		),
		array(
			'status'	=> 0
		)
	) )
);
=======
	// Exemplo de um UPDATE
	PDO4You::update( 'users', 
		array( array(
			array(
				'id' 		=> $_POST["id"]
			),
			array(
				'status'	=> 0
			)
		) )
	);
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
~~~ 


Excluindo um registro
---------------------
~~~ php
<<<<<<< HEAD
// Exemplo de um DELETE
PDO4You::delete( 'users', 
	array(
=======
	// Exemplo de um DELETE
	PDO4You::delete( 'users', 
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
		array(
			'id'		=> $_POST["id"]
		)
<<<<<<< HEAD
	)
);
=======
	);
>>>>>>> e07712c8ea0913e1a376030f54d1f0deb1deba33
~~~ 
