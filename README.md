# PDF Printer
This package is a wrapper for the private print-api package from [AMBERSIVE KG](https://ambersive.com). This package requires this endpoint otherwise you will not be able to create any pdf document.

## Installation

```bash
composer require ambersive/pdfprinter
```

## Usage

Please be aware that you will need a running instance of the [PRINT-API](https://github.com/AMBERSIVE/print-api). Otherwise the methods won't work as expected.

```php
// Setup the pdf printer
$printer  = new PdfPrinter($settings);
$printer->create("http://localhost:8080/pdf")->save("folder");
```

The full possiblities

```php
// Setup the pdf printer
$settings = new PdfPrinterSetting("http://localhost", 3000);
$printer  = new PdfPrinter($settings);
$options  = new PdfPrinterOption(
    $filename, 
    $postBackUrl,
    [], //$postBackBody 
    "" // $token
);

// Set auth header for basic authentication
$username = "test";
$password = "asdf";
$printer->authBasic($username, $password);

// Set auth header for basic authentication
$printer->authBearer("CUSTOM OR JWT TOKEN");

$printer->create("http://127.0.0.1:8000", null, function($instance, $result, $options, $successful) {
    // Will be executed after print execution
})->save('test', null, function($instance, $result, $filename, $path, $successful){
    // Do stuff after storing (even called if store was not successful)
});
```


## Security Vulnerabilities

If you discover a security vulnerability within this package, please send an e-mail to Manuel Pirker-Ihl via [manuel.pirker-ihl@ambersive.com](mailto:manuel.pirker-ihl@ambersive.com). All security vulnerabilities will be promptly addressed.

## License

This package is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## TODOS:
- Create tests
- Finsh the implementation of this package.