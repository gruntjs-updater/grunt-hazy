# grunt-hazy

> A grunt plugin that encrypt/encode/obfuscate your `javascript` and `php` files.




## Getting Started
This plugin requires Grunt `~0.4.2`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-hazy --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-hazy');
```

## The "hazy" task

### Overview
In your project's Gruntfile, add a section named `hazy` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
    hazy: {
        options: {
            // Task-specific options go here.
        },
        your_target: {
            // Target-specific file lists and/or options go here.
        }
    }
});
```

<!--### Options

#### options.separator
Type: `String`
Default value: `',  '`

A string value that is used to do something with whatever.

#### options.punctuation
Type: `String`
Default value: `'.'`

A string value that is used to do something else with whatever else.-->

### Sample Output
#### PHP

In this example, we have the basic setup. So if the `sample.php` file has the content : 

```php
<?php echo 'hello world'; ?>
```

The generated result would be :

```php
<?php eval("?>".base64_decode("PD9waHAgZWNobyAnaGVsbG8gd29ybGQnOyA/Pg==")."<?"); ?>
```
#### JAVASCRIPT

In this example, we have the basic setup. So if the `sample.js` file has the content :

```js
console.log('hello world');
```

The generated result would be :

```js
$=~[];$={___:++$,$$$$:(![]+"")[$],__$:++$,$_$_:(![]+"")[$],_$_:++$,$_$$:({}+"")[$],$$_$:($[$]+"")[$],_$$:++$,$$$_:(!""+"")[$],$__:++$,$_$:++$,$$__:({}+"")[$],$$_:++$,$$$:++$,$___:++$,$__$:++$};$.$_=($.$_=$+"")[$.$_$]+($._$=$.$_[$.__$])+($.$$=($.$+"")[$.__$])+((!$)+"")[$._$$]+($.__=$.$_[$.$$_])+($.$=(!""+"")[$.__$])+($._=(!""+"")[$._$_])+$.$_[$.$_$]+$.__+$._$+$.$;$.$$=$.$+(!""+"")[$._$$]+$.__+$._+$.$+$.$$;$.$=($.___)[$.$_][$.$_];$.$($.$($.$$+"\""+$.$$__+$._$+"\\"+$.__$+$.$_$+$.$$_+"\\"+$.__$+$.$$_+$._$$+$._$+(![]+"")[$._$_]+$.$$$_+"."+(![]+"")[$._$_]+$._$+"\\"+$.__$+$.$__+$.$$$+"('\\"+$.__$+$.$_$+$.___+$.$$$_+(![]+"")[$._$_]+(![]+"")[$._$_]+$._$+"\\"+$.$__+$.___+"\\"+$.__$+$.$$_+$.$$$+$._$+"\\"+$.__$+$.$$_+$._$_+(![]+"")[$._$_]+$.$$_$+"');"+"\"")())();
```

### Usage Examples
#### BASIC SETUP

```js
grunt.initConfig({
    hazy: {
        options: {},
        files: {
            'dest/sample.php': ['src/sample.php'],
            'dest/sample.js': ['src/sample.js']
        }
    }
});
```

#### PHP

```js
grunt.initConfig({
    hazy: {
        php: {
            expand: true,
            cwd: 'src',
            dest: 'dest',
            src: [ '*.php' ]
        }
    }
});
```
#### JAVASCRIPT

```js
grunt.initConfig({
    hazy: {
        js: {
            expand: true,
            cwd: 'src',
            dest: 'dest',
            src: [ '*.js' ]
        }
    }
});
```
#### ALL

```js
grunt.initConfig({
    hazy: {
        default_options: {
            options: {},
            files: {
                'dest/sample.php': ['src/sample.php'],
                'dest/sample.js': ['src/sample.js']
            }
        },
        php: {
            expand: true,
            cwd: 'src',
            dest: 'dest',
            src: [ '*.php' ]
        },
        js: {
            expand: true,
            cwd: 'src',
            dest: 'dest',
            src: [ '*.js' ]
        },
        all: {
            expand: true,
            cwd: 'src',
            dest: 'dest',
            src: [ '*.*' ]
        }
    }
});
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
- 0.1.5: Added javascript encoder
- 0.1.0: Initial release
