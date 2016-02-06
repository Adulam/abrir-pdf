<?php
session_start();
if(isset($_GET['archivo'])){
$archivo = $_GET['archivo'];
}else{
$archivo = "noexiste";
}


if(isset($_SESSION['pdf'])){
	
if($_SESSION['pdf'] == "nologueado"){
$fichero = "$archivo.pdf";
if (file_exists($fichero)) {
    header('Content-Type: application/pdf');
if(isset($_GET['descargar'])){
if($_GET['descargar'] == 1){
    header("Content-Disposition:attachment ; filename=[$archivo.pdf");		
}
}
    header('Expires: 0');
    header('Cache-Control: must-revalidate');
    header('Pragma: public');
    ob_clean();
    flush();

    readfile($fichero);

    exit;
}else{
echo "Archivo inexistente";
}

}else{
echo "No permitido";
}

}else{
echo "No autorizado";
}

