## How to run:

First thing you need to do is to run `make setup` to prepare you environment, that command you create a minikube cluster and install all the required dependency.

Right after this you should have all the pods up and running, you can check this by the output provided or running `kubectl -n kube-system get pods`.

## Grafana dashboard

Grafana give us the ability to see the data flow and the collected data, you can go to [Grafana UI](http://localhost:3000) and import [this dashboard](https://github.com/netobserv/network-observability-operator/blob/main/config/samples/dashboards/Network%20Observability.json).

## References
- [Network Observability Operator](https://github.com/netobserv/network-observability-operator)