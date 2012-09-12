# AVR Assembly Bundle for TextMate

This is a TextMate Bundle to help developing stuff in AVR Assembly used by Atmel AVR microcontrollers.

## Installation

The recommended way to install bundles is to use Git so you can update the bundle easily. To do so, open a Terminal, change to your bundle location and clone this repository:

    mkdir -p ~/Library/Application\ Support/TextMate/Bundles
    cd ~/Library/Application\ Support/TextMate/Bundles
    git clone git://github.com/mherb/avr-assembly.tmbundle

Alternatively you can also download the source as Zip or Tarball, extract it and place it into the bundle location noted above.

The above commands assume you're using TextMate 1. In case you have TextMate 2, then you have to use the bundle location

    ~/Library/Application\ Support/Avian/Pristine\ Copy/Bundles

instead of `~/Library/Application\ Support/TextMate/Bundles`.

If you're using TextMate 1 you should reload the bundles in TextMate using *Bundles -> Bundle Editor -> Reload Bundles*.

## Configuration

This bundle has commands for assembling and uploading your code to a device. In order to use those commands you have to configure them to suit your needs. This can be done by setting shell variables within TextMate (*TextMate -> Preferences -> Advanced -> Shell Variables*). If you are using TextMate 2 you can also set those variables in `.tm_properties` files (e.g. in your home directory or just for a certain project). See [here](http://wiki.macromates.com/Reference/FolderSpecificSettings) for details on how to use them in TextMate 2.

### Overview
<table>
  <tr>
    <th>Variable</th>
    <th>Default value</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>AVR_ASSEMBLER</code></td>
    <td><code>tavrasm -v "$TM_FILEPATH"</code></td>
    <td>The command to assemble source file to binary</td>
  </tr>
  <tr>
    <td><code>AVR_UPLOAD</code></td>
    <td><em>None</em></td>
    <td>The command to upload binary to target device (use with <code>$AVR_UPLOAD_FILE</code>)</td>
  </tr>
</table>


### Assemble command

This bundle has an *Assemble* command for assembling the currently opened file. The default assembler command used is `tavrasm`. If you'd like to use that assembler, please make sure the binary is in your `PATH`.

If you want to use another assembler, you can set that by changing the `AVR_ASSEMLBER` variable (see above). The value of this variable should be set to the shell command you would usually use to assemble a source file in the command line. However you have to replace the filepath with a placeholder. For instance, if you usually assemble using
    
    avra myfile.asm
    
then the *Value* should be set to

    avra "$TM_FILEPATH"
    
If you are using TextMate 2's `.tm_properties` files then the `$` should be escaped whith a backslash such as

    avra "\$TM_FILEPATH"
    
### Upload command

The upload command will upload the generated binary onto your target device. For instance, this can be done using [AVRDUDE](http://www.nongnu.org/avrdude/).

Because there is an infinte number of possible setups for your development environment (think of different target devices, programmers, ports and so on), this bundle does not provide a default upload command. Therefore you will have to configure the upload command yourself if you plan to use this feature.

The upload command can be set with the variable

    AVR_UPLOAD

You may want to use the variable

    $AVR_UPLOAD_FILE

within your upload command. This variable holds the path to the source file (the file you opened in TextMate) but **without** file the extension. This can be useful to determine the actual binary used for uploading. In most cases the extension of the generated binary should be `.hex`, but this may not be the case for you.

If you're usually programming your device with the command

    avrdude -p m8 -c avrisp -U flash:w:myfile.hex
    
then your upload command should look like this

    avrdude -p m8 -c avrisp -U flash:w:"$AVR_UPLOAD_FILE.hex" 

As with the assemble command, if you're using TextMate 2's `.tm_properties` files, then you have to escape the `$` in the variable name, otherwise this command will not work.
    
### Run command

The run command can be invoked using CMD-R and is simply the combination of the assembler and upload steps. Refer to the sections above for instructions on the individual commands.

## Contribution & Support

If you'd like to contribute to the bundle, please fork the repository, make some changes and send me a pull request. Pull requests are always welcome!

If you want to report a bug or request a feature, feel free to [open an issue](https://github.com/mherb/avr-assembly.tmbundle/issues).

## License

The MIT License (MIT)

Copyright (c) 2011-2012 [mherb](https://github.com/mherb)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.