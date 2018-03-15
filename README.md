# quantlib
quant library

Instructions to set up quantlib and quantlib-python on linux (ubuntu)

download latest version of quantlib from,
https://sourceforge.net/projects/quantlib/files/

untar the file
tar xzf QuantLib-1.12.tar.gz

cd QuantLib-1.12
./configure --prefix /home/foo/quantlib/QuantLib-1.12/qllib --with-boost-include=/home/foo/include --with-boost-lib=/home/foo/lib
Assuming boost library is installed under /home/foo
use --prefix option if the libraries (.so files) are to be installed on a directory different from the standard /usr/local


make


make install

files will be installed under /home/foo/quantlib/QuantLib-1.12/qllib

to test the library set up is working
cd Examples/BermudanSwaption

export LD_LIBRARY_PATH=/home/foo/quantlib/QuantLib-1.12/qllib/lib

g++ BermudanSwaption.cpp -o BermudanSwaption -lQuantLib

g++ BermudanSwaption.cpp -I/home/foo/quantlib/QuantLib-1.12 -o BermudanSwaption -L/home/foo/quantlib/QuantLib-1.12/qllib/lib -lQuantLib

./BermudanSwaption

To setup Quantlib-python

Download QuantLib-SWIG-1.12.tar.gz from https://sourceforge.net/projects/quantlib/files/QuantLib/1.12/other%20languages/
or the latest version
unzip and untar the file

cd QuantLib-SWIG-1.12

export PATH=$PATH:/path/to/quantlib/
path to quantlib install is required because configure looks for quantlib config.
./configure
make -C Python




