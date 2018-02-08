### Installing [exercism.io](http://exercism.io/) coding challenge using the Command-Line Interface (CLI)

#### Linux
Then download the [latest release](https://github.com/exercism/cli/releases/tag/v2.2.3). If you're unsure what archicture your processor has, the command ``uname -m`` should tell you.

Extract the binary using ``tar -xzvf FILENAME``, e.g.

    tar -xzvf exercism-linux-32bit.tgz
    
Place the binary in your PATH, e.g.:

    mkdir ~/bin
    mv exercism ~/bin/
    export PATH=$HOME/bin:$PATH
    
You will want to stick the export       ``PATH=$HOME/bin:$PATH`` line into your shell configuration. E.g. if your shell is bash, you could run:

    echo 'export PATH=$HOME/bin:$PATH' >> ~/.bashrc
    
To check which shell you have, run 
    
    echo $SHELL