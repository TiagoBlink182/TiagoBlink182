## Bem-vindo(a) ao perfil do TiagoBlink182 😁

 <div>
   <a href="https://github.com/TiagoBlink182">
   <img height="180em" src="https://github-readme-stats.vercel.app/api?username=TiagoBlink182&show_icons=true&theme=algolia&include_all_commits=true&count_private=true"/>
   <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=TiagoBlink182&layout=compact&langs_count=6&theme=algolia"/>

</div>
<div style="display: inline_block"><br>
  <img align="center" alt="Js" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
  <img align="center" alt="HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
  <img align="center" alt="CSS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">
  <img align="center" alt="Python" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original-wordmark.svg">
  <img align="center" alt="PyCharm" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pycharm/pycharm-original.svg">
  <img align="center" alt="VSCode" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg">
           
</div>
 
 <br>
 
  ### Para entrar em contato me segue nas redes abaixo!
 
<div> 
  <a href="https://www.youtube.com/channel/UCdgNFstc2PykTmdtNk0HjOw" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" target="_blank"></a>
  <a href="https://instagram.com/vgtiagobresolin" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
 <a href="https://discord.gg/5DVhGKVf4h" target="_blank"><img src="https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white" target="_blank"></a> 
  <a href = "mailto:tiagoblink182@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
  <a href="https://www.linkedin.com/in/vinhodogringo" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
 
  ![Snake animation](https://github.com/TiagoBlink182/TiagoBlink182/blob/output/github-contribution-grid-snake.svg)

</div>
 
 <!DOCTYPE html>
<html>
<head>
	<meta charset=utf-8 />
	<title>Contador de Visitas</title>

</head>
<body>

<?php

	function get_num_visitas(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}

		mysql_select_db("contador");
		$query = "SELECT total " .
				 "FROM `visitas` " .
				 "ORDER BY total ASC LIMIT 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		if (mysql_num_rows($result) == 0) {
			echo "No rows found, nothing to print so am exiting";
			exit;
		}
		$row = mysql_fetch_array($result);
		mysql_close($link);
		return $row["total"];
		//fazer consulta
		//retornar total
	}

	function imprime_visitas($contador){
		return "<h1>" . $contador . "</h1>";
	}

	function contar_visita(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}

		mysql_select_db("contador");
		$query = "UPDATE `visitas` " .
				 "SET total = total + 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		mysql_close($link);
	}

	contar_visita();
	$contador = get_num_visitas();
	echo imprime_visitas($contador);

?>


</body>
</html>
