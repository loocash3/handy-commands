#Serve movie

```php

$nameOfFile = 'FILENAME.mp4';
$filePath = './'.$nameOfFile;
header('Content-Description: File Transfer');
header('Content-Disposition: attachment; filename="'.$nameOfFile.'"');
header('Content-Type: application/force-download');
readfile($filePath);

```
