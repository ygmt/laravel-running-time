# laravel-running-time

[![Latest Stable Version](https://poser.pugx.org/y-ui/laravel-running-time/v/stable)](https://packagist.org/packages/y-ui/laravel-running-time)
[![Total Downloads](https://poser.pugx.org/y-ui/laravel-running-time/downloads)](https://packagist.org/packages/y-ui/laravel-running-time)
[![Latest Unstable Version](https://poser.pugx.org/y-ui/laravel-running-time/v/unstable)](https://packagist.org/packages/y-ui/laravel-running-time)
[![License](https://poser.pugx.org/y-ui/laravel-running-time/license)](https://packagist.org/packages/y-ui/laravel-running-time)

![Image](https://github.com/y-ui/y-ui.github.io/blob/master/table-20190815.png)

## Installation

    composer require ygmt/laravel-running-time dev-master
    
## Configuration
    
1. Open your `app/Http/Kernel.php` and add the following to `$middleware` array:

    ```php
    \RunningTime\Middleware\RunningTimeMiddleware::class,
    ```
 
2. Run the command below to publish the package config file `config/runningtime.php`:
 
    ```php
    php artisan vendor:publish --provider='RunningTime\RunningTimeServiceProvider'
    ```

- If you want to run with batch mode, this requires redis. open your `config/runningtime.php`:

    ```php
    'mode' => 'delay',
    ```
    
- If out of memory after running the command, open your `config/runningtime.php`:

    ```php
    'memory_limit' => '512M', //Modify to the appropriate value
    ```
    or run command with `--lessMemory`
    
## Usage
### Simple usage
```shell
#This will count the last 7 days of data
php artisan running-time

#This will show the top 20 path
php artisan running-time --line=20

php artisan running-time --start=2019-03-03

php artisan running-time --start='1 month ago'

php artisan running-time --path='your path'

#Significantly reduce memory usage but increase time spent
php artisan running-time --lessMemory
```


### Options

    --line  Maximum number of displayed lines
    --start Statistical start time
    --end   Statistical end time
    --path  Statistical path runtime
    --lessMemory Significantly reduce memory usage and increase time spent

## Clean log files
### Simple usage
```shell
php artisan running-time:clear --all

php artisan running-time:clear --recent=30
```    
    
    
## TODO LIST
 
- Web page

## License
laravel-running-time is an open-sourced software licensed under the MIT license.
