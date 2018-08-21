FROM wqael/notebooks:latest

RUN apt-get -qq update && \
    apt-get -qq install -y --no-install-recommends \
      git \
      python-opengl \
      xvfb \
      && \
    apt-get -qq clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip --no-cache-dir install -q -U \
      gym

RUN mkdir /JSAnimation && \
    cd /JSAnimation && \
    git clone https://github.com/jakevdp/JSAnimation && \
    cd JSAnimation && \
    python setup.py install && \
    rm -rf /JSAnimation

# TensorBoard
EXPOSE 6006
# IPython
EXPOSE 8888

WORKDIR /notebooks

# Allow rendering of OpenAI Gym in Jupyter
# https://gist.github.com/andrewschreiber/e9a21bba9c604a790e605fbacd3f4109
CMD ["xvfb-run -s \"-screen 0 1400x900x24\" jupyter notebook", "--allow-root", "--no-browser"]
