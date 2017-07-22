FROM golang
RUN curl -L  https://github.com/coreos/etcd/releases/download/v2.3.6/etcd-v2.3.6-linux-amd64.tar.gz -o etcd-v2.3.6-linux-amd64.tar.gz \
&& tar xzvf etcd-v2.3.6-linux-amd64.tar.gz \
&& cd etcd-v2.3.6-linux-amd64 \
&& cp etcd etcdctl /usr/bin/
EXPOSE 2379 2380 8848 8858 8870 
CMD nohup etcd &

