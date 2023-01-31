start-minikube:
	@minikube start

clone:
	@git clone https://github.com/netobserv/network-observability-operator.git nop

setup-nop: clone
	@cd nop && \
	$(MAKE) deploy deploy-loki deploy-grafana

deploy-sample-cr:
	@cd nop && \
	$(MAKE) deploy-sample-cr
setup-demo:
	@kubectl apply -f network-observability-operator/demo.yaml

setup: start-minikube setup-nop deploy-sample-cr setup-demo
	

destroy:
	@minikube delete && \
	rm -rf nop