## PDF out

Dieses Addon stellt den HTML to PDF converter DOMpdf zur Verfügung.

--

Nach der Instaalltion und Aktivierung des Addons kann folgendes am Anfang des
Ausgabe Templates eingegeben werden:

	<?php
	  // ?pdf=1
	  $print_pdf = rex_request('pdf', 'int');
	  use Dompdf\Dompdf;
	  if ($print_pdf) {
		  $art_pdf_name =  rex_string::normalize(rex_article::getCurrent()->getValue('name'));
		  header('Content-Type: application/pdf');

		  $dompdf = new Dompdf();
		  $dompdf->loadHtml('REX_ARTICLE[]');
		  $dompdf->setPaper('A4', 'landscape');
		  $dompdf->render();
		  $dompdf->stream($art_pdf_name);
		  die();
		}
	?>

Sofern dann an eine aufgerufenen URL **?pdf=1** angeängt wird wird der Inhalt von REX_ARTICLE[] als PDF ausgegeben.


___
### ToDo

siehe [ISSUES](https://github.com/FriendsOfREDAXO/pdfout/issues/)

___
### Changelog

siehe [CHANGELOG.md](CHANGELOG.md)

___
### Lizenz

siehe [LICENSE.md](LICENSE.md)
