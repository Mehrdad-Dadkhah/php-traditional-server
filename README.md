# PHP Traditional Endpoint Server

[![license](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)
[![Packagist](https://img.shields.io/packagist/dt/fineuploader/php-traditional-server.svg?maxAge=2592000)](https://packagist.org/packages/fineuploader/php-traditional-server)

PHP-based server-side example for handling traditional endpoint requests from Fine Uploader


php lib for use [fine-uploader js](https://fineuploader.com/) as client and upload big files with separate to chunks files.
This libarary is base on [chunks-uploader](https://github.com/Mehrdad-Dadkhah/chunks-uploader).


## Installation

```
composer require fineuploader/php-traditional-server
```

## Usage

```PHP
use FineUploader/Video/FineUploader;

$uploaderService = new FineUploader();
$uploadResult = $uploaderService->setConfigs(
                'form-input-name',
                'path-to-chunks-folder'
            )
                ->setUniqueIdentifier('unique-identifier')
                ->setDomain('http://example.com') //to set cors header
                ->checkDublicateFile(function($uuid) { //closure function to check file is duplicate or not it should get $uuid as input and return boolean. uuid is a video unique hash
                	return false;
                })
                ->upload('path-to-upload-directory');
```

## Custome file name

If want to set output file name try use setUploadName() function before fire finishUpload() function:
```PHP
$uploadResult = $uploadHandeler->setUploadName('my-name.mp4');
```
If don't set name your file name be with structur YYYY_m_d_hashname.mp4 and in final resutl generated name will be return.

## Check and generate output directory
If want to script make output directory automatically just set it:
```PHP
$uploadResult = $uploadHandeler->checkAndGenerateOutputDirectory();
```

For a step-by-step getting started guide, have a look at [the "Getting Started" section on our documentation site](http://docs.fineuploader.com/).
