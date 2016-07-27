FROM ubuntu:16.04

RUN apt-get update

RUN apt-get -y install python3 python3-setuptools python3-dev python python-dev python-setuptools sudo npm nodejs-legacy git libgdal-dev wget software-properties-common python3-pip python-pip

# RUN addgroup jupyter

RUN adduser jupyter --home /home/jupyter

RUN echo "jupyter:jupyter" | chpasswd

RUN mkdir /etc/jupyterhub

COPY jupyterhub_config.py /etc/jupyterhub/jupyterhub_config.py

RUN mkdir /usr/local/src/gdal-docker

# COPY . /usr/local/src/gdal-docker/

COPY sudo_jupyter /etc/sudoers.d/jupyter

COPY requirements.txt /usr/local/src/gdal-docker/jupyterhub_requirements.txt

RUN pip3 install -r /usr/local/src/gdal-docker/jupyterhub_requirements.txt --upgrade

RUN pip install jupyter ipython --upgrade

RUN ipython kernel install

RUN add-apt-repository ppa:ubuntugis/ubuntugis-unstable

# apt-get install -y gdal-bin

RUN apt-get -y install python3-numpy \
python3-gdal \
python3-matplotlib \
python3-pandas \
python-numpy \
python-gdal \
python-matplotlib \
python-pandas

RUN git clone https://github.com/granularag/pyspatial.git /usr/local/src/pyspatial

RUN /usr/local/src/pyspatial/scripts/requirements-ubuntu.sh 

RUN npm install -g configurable-http-proxy

RUN pip install -r /usr/local/src/pyspatial/requirements.txt

RUN cd /usr/local/src/pyspatial && python setup.py install

RUN usermod -a -G sudo jupyter

RUN pip install --upgrade psycopg2

RUN pip3 install --upgrade psycopg2

ENTRYPOINT ["jupyterhub", "-f", "/etc/jupyterhub/jupyterhub_config.py", "--no-ssl", "--ip", "0.0.0.0"]

# ENTRYPOINT ["python", "-m", "SimpleHTTPServer", "8080"]



