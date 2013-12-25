```
___________.___  ________.__          __          __        
\_   _____/|   |/  _____/|  |   _____/  |_       |__| ______
 |    __)  |   /   \  ___|  | _/ __ \   __\      |  |/  ___/
 |     \   |   \    \_\  \  |_\  ___/|  |        |  |\___ \ 
 \___  /   |___|\______  /____/\___  >__| /\ /\__|  /____  >
     \/                \/          \/     \/ \______|    \/ 

```

This project aims to fully implement the FIGfont spec in JavaScript. It works in the browser and with Node.js. You can see it in action here: http://patorjk.com/software/taag/ (the figlet.js file was written to power that application)

Quick Start - Node.js
-------------------------

Install:

```
npm install figlet
```

Simple usage:

```
var figlet = require('figlet');

figlet('Hello World!!', function(err, data) {
    if (err) {
        console.log('Something went wrong...');
        console.dir(err);
        return;
    }
    console.log(data)
});
```

That should print out:

```
  _   _      _ _        __        __         _     _ _ _ 
 | | | | ___| | | ___   \ \      / /__  _ __| | __| | | |
 | |_| |/ _ \ | |/ _ \   \ \ /\ / / _ \| '__| |/ _` | | |
 |  _  |  __/ | | (_) |   \ V  V / (_) | |  | | (_| |_|_|
 |_| |_|\___|_|_|\___/     \_/\_/ \___/|_|  |_|\__,_(_|_)
```

Basic Usage - Node.js
-------------------------

There are 3 main functions on the figlet object.

### text

Calling the figlet object as a function is shorthand for calling the text function. This method allows you to create ASCII Art from text. It takes in 3 parameters:

* Input Text - A string of text to turn into ASCII Art.
* Font Options - Either a string indicating the font name or an options object (description below).
* Callback - A function to execute with the generated ASCII Art.

Example:

```
figlet.text('Boo!', {
    font: 'Ghost',
    horizontalLayout: 'default',
    verticalLayout: 'default'
}, function(err, data) {
    if (err) {
        console.log('Something went wrong...');
        console.dir(err);
        return;
    }
    console.log(data);
});
```

That will print out:

```
.-. .-')                            ,---. 
\  ( OO )                           |   | 
 ;-----.\  .-'),-----.  .-'),-----. |   | 
 | .-.  | ( OO'  .-.  '( OO'  .-.  '|   | 
 | '-' /_)/   |  | |  |/   |  | |  ||   | 
 | .-. `. \_) |  |\|  |\_) |  |\|  ||  .' 
 | |  \  |  \ |  | |  |  \ |  | |  |`--'  
 | '--'  /   `'  '-'  '   `'  '-'  '.--.  
 `------'      `-----'      `-----' '--' 
```

#### Font Options

The font options object has 3 parameters which you can set:

* **font** - A string indicating the name of the font.
* **horizontalLayout** - One of the following strings: "default", "full", "fitted", "controlled smushing", "universal smushing" 
* **verticalLayout** - One of the following strings: "default", "full", "fitted", "controlled smushing", "universal smushing"

The layout options allow you to override a font's default "kerning". Below you can see how this effects the text. The string "Kerning" was printed using the "Standard" font with horiontal layouts of "default", "fitted" and then "full".

```
  _  __               _             
 | |/ /___ _ __ _ __ (_)_ __   __ _ 
 | ' // _ \ '__| '_ \| | '_ \ / _` |
 | . \  __/ |  | | | | | | | | (_| |
 |_|\_\___|_|  |_| |_|_|_| |_|\__, |
                              |___/ 
  _  __                   _               
 | |/ / ___  _ __  _ __  (_) _ __    __ _ 
 | ' / / _ \| '__|| '_ \ | || '_ \  / _` |
 | . \|  __/| |   | | | || || | | || (_| |
 |_|\_\\___||_|   |_| |_||_||_| |_| \__, |
                                    |___/ 
  _  __                        _                 
 | |/ /   ___   _ __   _ __   (_)  _ __     __ _ 
 | ' /   / _ \ | '__| | '_ \  | | | '_ \   / _` |
 | . \  |  __/ | |    | | | | | | | | | | | (_| |
 |_|\_\  \___| |_|    |_| |_| |_| |_| |_|  \__, |
                                           |___/ 
```

In most cases you'll either use the default setting or the "fitted" setting. You'll probably never want to use the smushing options, but they are included out of completeness (see the FIGlet spec in the doc folder for information on smushing).

### metadata

The metadata function allows you to retrieve a font's default options and header comment. Example usage:

```
figlet.metadata('Standard', function(err, options, headerComment) {
    if (err) {
        console.log('something went wrong...');
        console.dir(err);
        return;
    }
    console.dir(options);
    console.log(headerComment);
});
```

### fonts

The fonts function allows you to get a list of all of the available fonts. Example usage:

```
figlet.fonts(function(err, fonts) {
    if (err) {
        console.log('something went wrong...');
        console.dir(err);
        return;
    }
    console.dir(fonts);
});
```


Getting Started - The Browser
-------------------------

The browser API is the same as the Node API with the exception of the "fonts" method not being available. The browser version also requires jQuery (any version should work as it only utilizes the ajax method for its loadFont function).

Example usage:

```
<script type="text/javascript" src="jquery-1.7.2.min.js"></script>
<script type="text/javascript" src="figlet.js"></script>
    
<script>

    figlet(inputText, 'Standard', function(err, text) {
        if (err) {
            console.log('something went wrong...');
            console.dir(err);
            return;
        }
        console.log(text);
    });

</script>
```

See the examples folder for a more robust front-end example.
