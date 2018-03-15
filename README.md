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
make -C Python install 

This will install python packages into the default python location, ( it could be the anaconda directory id anaconda is setup), example directory.
/home/foo/anaconda2/lib/python2.7/site-packages/QuantLib_Python-1.12-py2.7-linux-x86_64.egg

export PYTHONPATH=$PYTHONPATH:/home/foo/anaconda2/lib/python2.7/site-packages/QuantLib_Python-1.12-py2.7-linux-x86_64.egg/QuantLib

make -C Python check
if PYTHONPATH is not set, running the above command will fail with a message,
ImportError: No module named _QuantLib

if the command make -C Python check fails with a message,
ImportError: /home/sanurhea/anaconda2/bin/../lib/libstdc++.so.6: version `GLIBCXX_3.4.21' not found
 
 install package libgcc
 conda install libgcc
 
 




 


