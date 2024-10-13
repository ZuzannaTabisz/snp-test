FROM python:3.9 AS backend

WORKDIR /usr/src/backend


COPY . .


RUN apt-get update && apt-get install -y \
    build-essential \
    wget \
    cmake \
    git \
    libboost-all-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/backend/pipeline

# tar -xzf ViennaRNA-2.6.4.tar.gz \

RUN cd ViennaRNA-2.6.4 \
    && ./configure \
    && make \
    && make install \
    && cd .. \
    && rm -rf ViennaRNA-2.6.4 ViennaRNA-2.6.4.tar.gz

WORKDIR /usr/src/backend

RUN pip install --no-cache-dir -r requirements.txt


RUN chmod -R 777 pipeline && ls -ld pipeline

EXPOSE 8080


CMD ["python", "app.py"]
