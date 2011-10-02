# AVR Assembly Bundle for TextMate

This is a TextMate Bundle to help developing stuff in AVR Assembly used by Atmel AVR microcontrollers.

## Installation

### Install with Git

    mkdir -p ~/Library/Application\ Support/TextMate/Bundles
    cd ~/Library/Application\ Support/TextMate/Bundles
    git clone git://github.com/mherb/avr-assembly.tmbundle
    
After doing so, you should reload the bundles in TextMate using *Bundles -> Bundle Editor -> Reload Bundles*

### Install without Git
  
If you don't want to use Git to install the bundle, you can also download the source as Zip or Tarball, extract the archive and rename the extracted folder to *avr-assembly.tmbundle*. Then move the folder to

    ~/Library/Application\ Support/TextMate/Bundles

After doing so, you should reload the bundles in TextMate using *Bundles -> Bundle Editor -> Reload Bundles*

## Assemble command configuration

This bundle has an *Assemble* command for assembling the currently opened file. The default assembler command used is `tavrasm`. If you'd like to use that assembler, please make sure the binary is in your `PATH`.

If you want to use another assembler, you can configure the command used by setting a shell variable in TextMate. Therefore go to *TextMate -> Preferences -> Advanced -> Shell Variables*, click the plus-sign and enter as *Variable*

    AVR_ASSEMBLER
    
*Value* should be set to the shell command you would usually use to assemble a source file in the command line. However you have to replace the filepath with a placeholder. For instance, if you usually assemble using
    
    avra myfile.asm
    
then the *Value* should be set to

    avra "$TM_FILEPATH"

## Contribution & Support

If you'd like to contribute to the bundle, please fork the repository, make some changes and send me a pull request. Pull requests are always welcome!

If you want to report a bug or request a feature, feel free to [open a issue](https://github.com/mherb/avr-assembly.tmbundle).

## License

The MIT License (MIT)

Copyright (c) 2011 [mherb](https://github.com/mherb)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.