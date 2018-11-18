FROM python:3
MAINTAINER Constantine Korikov "constantine.koriko.v+simket(at)gmail.com"

# System dependencies
RUN apt-get update
RUN apt-get install -y apt-utils
RUN apt-get install -y vim
RUN apt-get install -y wget
RUN apt-get install -y python3-pip

# For pyverilog
RUN apt-get install -y iverilog
RUN apt-get install -y graphviz

RUN pip3 install Cython
RUN pip3 install numpy
RUN pip3 install scipy
RUN pip3 install matplotlib 
RUN pip3 install qutip 
RUN pip3 install pytest
RUN pip3 install pylint
RUN pip3 install pygraphviz

# Jupiter
RUN pip3 install ipykernel
RUN pip3 install jupyter 

RUN python3 -m ipykernel.kernelspec

# Configure container
EXPOSE 8888
WORKDIR /work
RUN mkdir -p /work/simket
RUN jupyter notebook --generate-config

# Checkout repo
RUN git clone https://github.com/PyHDI/Pyverilog.git

ENTRYPOINT ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root"]
