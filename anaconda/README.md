### Overview

* Base: ubuntu
* Version: Python 2
* Location: `opt/anaconda`

### Jupyter Notebook

#### Simple Bridge

* `docker run -it -p 8888:8888 colinfang/anaconda jupyter notebook --ip 0.0.0.0 --no-browser`
* Visit `127.1.2.3:8888` in the host.

#### Customized Bridge

* `docker run -it -p 127.0.0.1:1234:5678 colinfang/anaconda jupyter notebook --ip '*' --port 5678 --no-browser`
* Visit `127.0.0.1:1234` in the host.
* This also allows remote clients to connect via host_ip:1234.

#### Simple Host (Ad Hoc)

* `docker run -it --net host colinfang/anaconda jupyter notebook --no-browser`
* Visit `127.0.0.1:8888` in the host.

#### Fix

* Due to a [bug](https://github.com/ipython/ipython/issues/7062), we have to use the following otherwise the kernel dies:
* `docker run -it -p 8888:8888 colinfang/anaconda sh -c "jupyter notebook --ip 0.0.0.0 --no-browser"`