# ARGO ROLLOUTS

Argo Rollouts agrega nuevas estrategias de deploy como canary o blugreen.

## Documentación

    https://argoproj.github.io/argo-rollouts/

## Instalación de Argo Rollouts

### Instalación como controlador

    kubectl create namespace argo-rollouts

    kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

### Instalación con Helm

Descargar el helm chart

    helm repo add argo https://argoproj.github.io/argo-helm
    helm install my-release argo/argo-rollouts

Mi alternativa Gitops

    helm repo add argo https://argoproj.github.io/argo-helm 
    helm pull argo/argo-rollouts --untar
 


### Kubectl Plugin

    brew install argoproj/tap/kubectl-argo-rollouts
