FROM python:3
MAINTAINER Constantine Korikov "constantine.koriko.v+simket(at)gmail.com"

# System dependencies
RUN apt-get update && \
    apt-get install -y apt-utils   \
                       vim         \
                       wget        \
                       python3-pip \
                       # For pyverilog
                       iverilog    \
                       graphviz    \
                   && rm -rf /var/lib/apt/lists/*

# Configure container
WORKDIR /app/simket

# Python dependencies
ADD requirements.txt /app
RUN pip3 install -r /app/requirements.txt
RUN pip3 install qutip
RUN python3 -m ipykernel.kernelspec

# Configure container (again)
WORKDIR /app/
RUN jupyter notebook --generate-config

# Checkout repos
RUN git clone https://github.com/PyHDI/Pyverilog.git
RUN git clone https://github.com/myhdl/myhdl.git

EXPOSE 8888

ENTRYPOINT ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root"]
