# Automatic Speech Recognition (ASR) For Asterisk using Google Speech

This EAGI use the File Descriptor to get the audio in realtime and perform one simple VAD analise in the signal ... 

## Dependencies

- flac >= 1.2.1
- libflac-dev >= 1.2.1
- libsndfile >= 1.0.21
- libsndfile-dev >= 1.0.21
- audiolab >= 0.11.0

## Installation

On Debian and Ubuntu based operating systems :

```sh
apt install -y libflac-dev flac \
    python-numpy python-scipy python-dev python-setuptools \
    libsndfile-dev
or 
sudo apt install python3-numpy python3-scipy python3-matplotlib python3-pandas python3-sympy python3-nose
apt install -y libflac-dev flac  python-dev python-setuptools libsndfile-dev
pip install scikits.audiolab==0.11.0
wget https://bootstrap.pypa.io/pip/2.7/get-pip.py
python2 get-pip.py
python2.7 -m pip install numpy
python2.7 -m pip install scipy
    ##install wave module
    wget http://www.mega-nerd.com/libsndfile/files/libsndfile-1.0.25.tar.gz
    tar -xzf libsndfile-1.0.25.tar.gz
    cd libsndfile-1.0.25
    ./configure
    make -j8
    make -j8 install
   
    wget --no-check-certificate https://pypi.python.org/packages/source/s/scikits.audiolab/scikits.audiolab-0.11.0.tar.gz#md5=f93f17211c7763d8631e0d10f37471b0
    tar -xzf scikits.audiolab-0.11.0.tar.gz
    cd scikits.audiolab-0.11.0
    python setup.py build
    python setup.py install
python2.7 -m pip install scikits.audiolab
```


Download and install audiolab from: http://pypi.python.org/pypi/scikits.audiolab/

## Examples

### How use in dialplan from Asterisk

`extensions.conf` :

```asterisk
exten=>_11111111,1,Answer()
exten=>_11111111,n,eagi,pahh.py
exten=>_11111111,n,GotoIf($[${EXISTS(${GoogleUtterance})}]?hello:bye)
exten=>_11111111,n(hello),NoOP(You Said = ${GoogleUtterance})
exten=>_11111111,n(bye),Hangup()
```
