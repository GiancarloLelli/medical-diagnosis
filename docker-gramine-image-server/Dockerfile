FROM registry.hub.docker.com/gramineproject/gramine:latest

#RUN apt-get update && apt-get install -y python3-pip gcc make
RUN apt-get install -y python3-pip gcc make

WORKDIR /usr/src/app

COPY . ./

# generate private key
RUN gramine-sgx-gen-private-key
# genereate required sgx manifest and signature
RUN make SGX=1

RUN pip install --no-cache-dir -r requirements.txt

CMD ["gramine-sgx ./python3 -u image-server.py"]