# SRE Observability Lab

Running lab:
```
docker compose --profile all up
```


## Architecture
```mermaid
graph TB;
  subgraph App
    A(Frontend)-->A1{random:};
    A1-->B1(Backend Fast);
    A1-->B2(Backend Medium);
    A1-->B3(Backend Slow);
  end
  subgraph OTLP
    direction TB
    P[(Prometheus)].->B1;
    P.->B2;
    P.->B3;
    G(Grafana)-->P;
    O[otel-collector]-->P;
    P-->O;
    O-->J(Jaeger);
  end
```

## Links
- [Grafana](http://localhost:3000/) (admin/admin)
- [Prometheus](http://localhost:9090)
- [Jaeger](http://localhost:16686/search)
- [Frontend](http://localhost:4000/api/v1/frontend)
- [Backend Fast](http://localhost:4001/api/v1/calc/sum/2/2)
- [Backend Medium](http://localhost:4002/api/v1/calc/sum/2/2)
- [Backend Slow](http://localhost:4003/api/v1/calc/sum/2/2)
