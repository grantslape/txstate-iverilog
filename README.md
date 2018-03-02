# txstate-iverilog
This repo is to help CS3339 students at Texas State University learn the basics of modeling hardware with Icarus Verilog and GTKWave.

There is an installation guide located at http://iverilog.wikia.com/wiki/Installation_Guide where much of this information is derived from.  Basic familiarity with the command line is assumed.

## Usage
You can check out the basic user guide [here](http://iverilog.wikia.com/wiki/User_Guide).  Included in this repository are some basic files: a hello world and a counter.  If you are getting this from another source, check out [this article](http://iverilog.wikia.com/wiki/Getting_Started) where the files are also listed:
```shell
$ iverilog -o hello.out hello.v
$ vvp hello.out
Hello World!
```

Check out the advanced usage at the end to use both _iverilog_ and _gtkwave_.

## MacOS Installation

1. [install Homebrew](https://brew.sh/)
2. Run the following shell command to install iverilog:
```shell  
$ brew install icarus-verilog
```  

### GTKwave

GTKwave is hosted here: http://gtkwave.sourceforge.net/.  However at the time of this writing, Sourceforge has been down for more than 24 hours, so alternative sources must be sought out:

There are two methods of MacOS installation for GTKWave.  The easiest is install with a package manager.  Unfortunately when I tried this most recently with Homebrew, there were checksum issues with the package.

2. Run the following shell command:  
```shell  
$ brew tap caskroom/cask
$ brew install caskroom/cask/gtkwave
```  
3. That probably didn't work so let's try to manually install.

#### Other Method
1. Download [GTKwave](https://github.com/grantslape/txstate-iverilog/raw/master/gtkwave.zip) from a kind individual
2. Unzip the application and move it to your Applications folder:
```shell
$ unzip gtkwave.zip  
$ mv -r gtkwave.app /Applications/  
```  
3. The application is ready to go now, if you like you can set GTKwave up to be invoked from the command line:
```shell
$ cpan install Switch
$ /Applications/gtkwave.app/Contents/Resources/bin/gtkwave foo.vcd
```

## Linux Installation
1. Installation here depends on your flavor.  apt-get will be easiest but you will need root.  Try these first:
```shell  
$ sudo apt-get install verilog
$ sudo apt-get install gtkwave  
```  
2. If this is unsuccessful you may need to download the source code from Github and compile it locally.  There is an [installation guide](http://iverilog.wikia.com/wiki/Installation_Guide) that is very helpful.

## Advanced Usage

Now let's tie it all together:
1. Make sure you have `counter.v` and `counter_tb.v`.
2. Run the following:  
```shell  
$ iverilog -o counter_chip.out counter_tb.v counter.v  
$ vvp counter_chip.out  
```  
3. Now we can invoke GTKwave to view the waveform output of our simulated counter.  The path of GTKwave is dependant on your system.  I recommend just aliasing it to _gtkwave_ in your shell:  
```shell  
$ /Applications/gtkwave.app/Contents/Resources/bin/gtkwave test.vcd
```  
4. This should open the GUI application.  Click "test" in the upper left and expand.
5. Right click on c1 and choose "Insert"
6. You should see the clock, out, and reset waves in the viewer.

