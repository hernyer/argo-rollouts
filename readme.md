# ARGO ROLLOUTS

Argo Rollouts agrega nuevas estrategias de deploy como canary o blugreen.

## Documentación

    https://argoproj.github.io/argo-rollouts/
    https://codefresh.io/learn/argo-rollouts/
    https://blog.baeke.info/2021/11/01/kubernetes-blue-green-deployments-with-argo-rollouts/

## Instalación de Argo Rollouts

### Instalación como controlador

    kubectl create namespace argo-rollouts

    kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

### Instalación con Helm

Descargar el helm chart

    helm repo add argo https://argoproj.github.io/argo-helm
    helm install my-release argo/argo-rollouts

### Mi alternativa Gitops con Helm

1. Creo un repo en GH.

        https://github.com/hernyer/argo-rollouts.git

2. Descargo el chart de argo-rollouts y subo al repo.

        helm repo add argo https://argoproj.github.io/argo-helm 
        helm pull argo/argo-rollouts --untar

3. Creo un archivo value-prod.yaml y modifico los siguientes valores:

        dashboard:
            # -- Deploy dashboard server
            enabled: true

        service:
            # -- Sets the type of the Service
            type: LoadBalancer

4. En argo-cd creo una app argo-rollouts en el ns argo-rollouts sincronizada al repo de gh donde esta el value-prod.yaml

5. En la siguiente url levanta un dashboard de argo rollouts.

    <http://localhost:3100/rollouts>

### Kubectl Plugin

    brew install argoproj/tap/kubectl-argo-rollouts

## Canary Strategy

## Bluegreen Strategy

La estrategia bluegreen utiliza 2 servicios (sevicio active y servicio preview), con dos replica set y cada uno con sus pods.

Creo un ns rollout-bluegreen, con argocd levanto la app asociada a GH donde está el rollout.yaml (deployment y 2 servicios).

¿La aplicación blue y yello deben correr en el mismo puerto? Ahora corren en 89 blue y 90 yellow con loadbalancer para ver los cambios.

Opciones disponibles

    abort:
    rollback: 
    promote:
