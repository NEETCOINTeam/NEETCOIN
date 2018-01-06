## How to build for Mac OS X ##

Supported OS　10.11 El capitan or later  
(It is recommended that you compile with the OS you are using.)

homebrew
http://brew.sh/
  
brew install openssl qt5 berkeley-db@4 miniupnpc  
brew install homebrew/versions/boost160

## Compile

### NEETCOIN-QT

cd NEETCOIN  
qmake  
make  
macdeployqt NEETCOIN-qt.app

### NEETCOINd

cd NEETCOIN/src  
make -f makefile.osx
