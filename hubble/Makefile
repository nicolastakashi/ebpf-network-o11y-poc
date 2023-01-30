start-minikube:
	@minikube start --network-plugin=cni --cni=false

install-cilium:
	@helm upgrade -i cilium cilium/cilium --namespace kube-system \
	--set=operator.replicas=1 --reuse-values \
   	--set hubble.relay.enabled=true \
   	--set hubble.ui.enabled=true

restart-unmanaged-pods:
	@kubectl get pods --all-namespaces -o custom-columns=NAMESPACE:.metadata.namespace,NAME:.metadata.name,HOSTNETWORK:.spec.hostNetwork --no-headers=true | grep '<none>' | awk '{print "-n "$$1" "$$2}' | xargs -L 1 -r kubectl delete pod

sleep:
	sleep 60

setup: start-minikube install-cilium sleep restart-unmanaged-pods
	@kubectl -n kube-system get pods

port-forward-relay:
	@kubectl -n kube-system port-forward svc/hubble-relay 4245:80

port-forward-ui:
	@kubectl -n kube-system port-forward svc/hubble-ui 12000:80

test-connectivity:
	@while true; do cilium connectivity test; done

destroy:
	@minikube delete