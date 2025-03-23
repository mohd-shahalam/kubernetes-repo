# kubernetes-repo

# kubernetes-repo

Steps to Create k8s cluster with 2 nodes on ubuntu server using Kind.
1. sudo apt update && sudo apt upgrade -y
2. sudo apt install -y docker.io
3. sudo systemctl start docker && sudo systemctl enable docker
5. sudo usermod -aG docker $USER
6. Reboot the server
7. curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-amd64
8. chmod +x ./kind && sudo mv ./kind /usr/local/bin/
9. Verify installation:  kind version
10. Install kubectl : curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
11. chmod +x ./kubectl && sudo mv ./kubectl /usr/local/bin/
12. Verify: kubectl version --client
13. Create a Kind Configuration File: nano kind-2node.yaml and add below content
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker

14. kind create cluster --name two-node-cluster --config kind-2node.yaml
15. Verify the Cluster: kubectl cluster-info --context kind-two-node-cluster
16. List the nodes: kubectl get nodes
