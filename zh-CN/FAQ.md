---
id: FAQ
title: FAQ
sidebar_label: FAQ
---

# 常见问题

### Milvus是什么？

  Milvus是一款面向向量检索的数据库系统，可以很好的运行和部署在x86架构的服务器环境和主流的虚拟化环境下，也支持目前主流的网络硬件设备。操作系统方面，Milvus支持目前主流的Linux操作系统环境。

### Milvus能够使用的接口有哪些？

  目前Milvus提供Python和C++的SDK接口，同时还支持所有基于Thrift的通信方式。

### Milvus的易用性如何？

  Milvus的使用非常简单。可以把Milvus当作普通的数据库系统，具体参考前文提供的样例程序和https://pypi.org/project/pymilvus/ 。

### Milvus具备高可用特性吗？

  Milvus集群具备高可用性，其存储和计算等集群均容许部分组件失效，而不影响整个集群的使用。

### 向量存入Milvus后，如何检索？

  向量存入Milvus后，Milvus会给对应向量一个ID，用户需要自己将该向量ID和其对应的其他属性存入另外一个数据库系统。查询的时候，用户提供需要查询的向量，Milvus会返回和用户提供向量最匹配的数个向量的ID以及匹配度。

### 如何选择向量索引的类型？

  依据用户的需求，您可以选择以下索引类型：

- Flat类型

  如果需求精确匹配，那么请选择Flat类型索引。精确匹配，可以为用户提供100%精确匹配的向量，但是由于计算量巨大，性能影响也很大。

- IVFFlat类型

  如果不追求100%精确匹配，可以选择IVFFlat类型索引，支持大数据量的高精度匹配。

- IVFSQ类型

  运用scalar quantization的向量索引，能大幅缩小向量体积（大概缩减3/4），从而能有效提高向量吞吐量。

### Milvus是否支持边插入边查询的能力？

  支持。如果您想在Milvus里边插入向量边查询，建议在 *home/$USER/milvus/conf/server_config.yaml* 下的 *cache_config*区域，将参数"insert_cache_immediately"设置为'True'。

### 数据存储在哪里？

  向量数据可以存储在您的本地磁盘，或是MinIO云上。若要了解更多，请阅览[数据存储](userguide/data_storage.md).