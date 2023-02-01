start-minikube:
	@minikube start --iso-url https://storage.googleapis.com/minikube-performance/minikube.iso
	
	
install-svc-monitor-crd:
	@kubectl apply -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/main/example/prometheus-operator-crd/monitoring.coreos.com_servicemonitors.yaml

download-yaml-package:
	@curl -O https://k8s-bpf-probes-public.oss-cn-hangzhou.aliyuncs.com/kindling-install.tar && \
	tar -xvf kindling-install.tar && cd kindling-install && \
	sh install.sh

setup: start-minikube install-svc-monitor-crd download-yaml-package

setup-demo:
	@kubectl apply -f kindling/demo.yaml

destroy:
	@minikube delete && \
	rm -rf kindling-install.tar kindling-install