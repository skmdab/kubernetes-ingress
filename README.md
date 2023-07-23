# NGINX Ingress Controller Setup

## Prerequisites
Ensure you have `kubectl` and the appropriate Kubernetes context configured.

## Installation Steps

0. Navigate to the deployments directory:

git clone https://github.com/skmdab/kubernetes-ingress.git

cd kubernetes-ingress/deployments

1. Create a namespace and a service account for the NGINX Ingress Controller:

kubectl apply -f common/ns-and-sa.yaml

2. Create a cluster role and cluster role binding for the service account:

kubectl apply -f rbac/rbac.yaml

3. Create a secret with a TLS certificate and a key for the default server in NGINX:

kubectl apply -f secrets/default-server-secret.yaml

4. Create a config map for customizing NGINX configuration:

kubectl apply -f common/nginx-config.yaml

5. Create an IngressClass resource (uncomment annotations to set it as the default IngressClass):

kubectl apply -f common/ingress-class.yaml

6. Apply the DaemonSet:

kubectl apply -f daemon-set/nginx-ingress.yaml

7. Apply the AWS ELB service configuration (Modify the file as needed):

kubectl apply -f service/loadbalancer-aws-elb.yaml




