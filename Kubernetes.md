# Apostila de Kubernetes 🚀

O Kubernetes é uma plataforma de código aberto para automatizar a implantação, o dimensionamento e o gerenciamento de aplicativos em contêineres. Nesta apostila, vamos explorar os conceitos, componentes e exemplos de uso do Kubernetes.

## Introdução ao Kubernetes

O Kubernetes, frequentemente abreviado como K8s, simplifica e automatiza o processo de implantação, dimensionamento e gerenciamento de aplicativos em contêineres. Ele fornece uma plataforma robusta para orquestrar contêineres e lidar com a complexidade de ambientes distribuídos.

## Componentes do Kubernetes

O Kubernetes consiste em vários componentes que trabalham juntos para fornecer funcionalidades poderosas:

- **Pods**: A menor unidade em Kubernetes, que contém um ou mais contêineres.
- **Deployments**: Gerencia a implantação e a atualização de aplicativos em contêineres.
- **Services**: Fornece um ponto de acesso estável para os aplicativos, permitindo a comunicação entre diferentes partes do sistema.
- **Nodes**: São as máquinas físicas ou virtuais onde os pods são executados.
- **Master Node**: Gerencia e controla o cluster Kubernetes, coordenando a execução de pods nos nós.

## Exemplo de Aplicação: Implantação de um Aplicativo Web

Vamos ver como podemos implantar um aplicativo web simples no Kubernetes. Aqui está um exemplo de um arquivo de configuração YAML para um Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: nginx:latest
        ports:
        - containerPort: 80

```
- `apiVersion`: Especifica a versão da API do Kubernetes que será utilizada para criar o recurso. Neste caso, estamos usando a versão `apps/v1`.
- `kind`: Define o tipo de recurso que estamos criando, que neste caso é um Deployment.
- `metadata`: Contém metadados sobre o recurso, como nome, namespace, rótulos, etc.
  - `name`: Define o nome do Deployment, que é `my-app`.
- `spec`: Define as especificações para o Deployment, incluindo o número de réplicas, o seletor e o template dos pods.
  - `replicas`: Especifica o número desejado de réplicas do pod. Neste exemplo, estamos configurando para 3 réplicas.
  - `selector`: Define como os pods são selecionados para o Deployment.
    - `matchLabels`: Define os rótulos que devem ser correspondidos para selecionar os pods. Neste caso, estamos selecionando pods com o rótulo `app: my-app`.
  - `template`: Define o modelo para os pods que serão criados pelo Deployment.
    - `metadata`: Metadados para o template do pod.
      - `labels`: Rótulos para o pod.
        - `app: my-app`: Define o rótulo `app` como `my-app`.
    - `spec`: Especificações para os containers dentro do pod.
      - `containers`: Lista os containers dentro do pod.
        - `name: my-app`: Nome do container.
        - `image: nginx:latest`: Imagem Docker a ser usada para o container. Neste caso, estamos usando a imagem mais recente do Nginx.
        - `ports`: Lista de portas que o container expõe.
          - `containerPort: 80`: Porta que o container está escutando, neste caso, a porta 80.

Este código YAML define um Deployment no Kubernetes chamado `my-app`, que cria três réplicas de um pod contendo um contêiner Nginx. O contêiner expõe a porta 80 para tráfego de entrada.

