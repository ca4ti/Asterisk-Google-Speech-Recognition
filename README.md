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
