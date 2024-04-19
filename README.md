# Criando-um-Deploy-de-uma-Aplica-o

Para realizar o deploy de uma aplicação completa com frontend, backend e database MySQL no Kubernetes, precisaremos seguir alguns passos importantes. Aqui está um guia geral que pode nos ajudar:

1. **Desenvolvimento Local**:
   - Desenvolva o frontend e o backend localmente e garanta que eles funcionem como esperado.
   - Configure o MySQL localmente para testar a integração com o backend.

2. **Criação de Imagens Docker**:
   - Crie uma imagem Docker para o frontend e outra para o backend.
   - Utilize um `Dockerfile` para definir as configurações necessárias para cada serviço.
   - Não se esqueça de criar uma imagem para o MySQL, ou podemos optar por usar uma imagem oficial do Docker Hub.

3. **Configuração do Kubernetes**:
   - Escreva os arquivos de configuração do Kubernetes (YAML) para cada um dos serviços.
   - Defina os `Deployments` para o frontend e o backend.
   - Configure um `Service` para expor o frontend e o backend.
   - Configure um `PersistentVolume` e um `PersistentVolumeClaim` para o armazenamento do MySQL.

4. **Deploy no Kubernetes**:
   - Utilize o `kubectl` para aplicar as configurações e criar os serviços no cluster do Kubernetes.
   - Monitore os serviços com `kubectl get pods`, `kubectl logs` e outros comandos úteis.

5. **Testes e Validação**:
   - Teste a aplicação para garantir que tudo está funcionando corretamente.
   - Valide a comunicação entre o frontend, o backend e o banco de dados.

6. **Pronto para Produção**:
   - Após a validação, sua aplicação estará pronta para ser movida para um ambiente de produção.

Lembre-se de que cada um desses passos pode ter subetapas específicas, dependendo das particularidades do seu projeto. 

Aqui está um exemplo básico de um arquivo YAML para um **Deployment** no Kubernetes. Este arquivo define um Deployment chamado `meu-app`, que gerencia um conjunto de pods com base em uma imagem `nginx`.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: meu-app
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.17.1
        ports:
        - containerPort: 80
```

Neste exemplo, o `apiVersion` define a versão da API do Kubernetes que estamos usando. O `kind` especifica que é um Deployment. Dentro do `metadata`, definimos o nome e as labels do Deployment. A seção `spec` contém a especificação do Deployment, incluindo o número de `replicas` desejadas, o `selector` para identificar os pods que fazem parte deste Deployment, e o `template` do pod, que inclui a definição dos containers que serão executados, neste caso, um container `nginx` na versão `1.17.1` que expõe a porta `80`.

Espero que este exemplo te ajude a começar com seus próprios arquivos YAML para o Kubernetes.

https://github.com/denilsonbonatti/k8s-projeto1-app-base

https://docs.google.com/presentation/d/1sy2twjdQiZGR71nY4zPSKm6R_q2h5D4lDycmxOxRhk4/edit?pli=1#slide=id.p1
