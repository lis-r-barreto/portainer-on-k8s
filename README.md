# Kubernetes Cluster com k3s, k3d e Portainer

Este repositório demonstra como configurar um cluster Kubernetes local usando k3s, k3d, e gerenciar visualmente os recursos usando o Portainer.

## Pré-requisitos

Certifique-se de ter instalado os seguintes componentes:

- [Docker](https://www.docker.com/)
- [k3d](https://k3d.io/)

# Kubernetes Cluster com k3s, k3d e Portainer

Este repositório inclui manifestos YAML para criar e configurar um ambiente Kubernetes local usando k3s e k3d, juntamente com o gerenciamento visual do Portainer.

## Manifestos:

- **Namespace:**
  - Namespace `portainer` foi criado para isolar recursos relacionados ao Portainer.

- **ServiceAccount:**
  - ServiceAccount `portainer-sa-clusteradmin` foi criado para atribuir permissões ao Portainer.

- **PersistentVolumeClaim (PVC):**
  - PVC `portainer` foi criado para persistência de dados do Portainer.

- **ClusterRoleBinding (RBAC):**
  - RBAC `portainer` foi criado para conceder permissões de administrador de cluster ao ServiceAccount do Portainer.

- **Service:**
  - Service `portainer` foi criado como NodePort para expor o Portainer externamente.

- **Deployment:**
  - Deployment `portainer` foi criado para gerenciar a implantação e a escalabilidade do Portainer.

## Como Usar:

1. **Crie o cluster com k3d:**
   ```bash
   k3d cluster create portainer-cluster
   ```

3. **Aplique os manifestos para deploy do Portainer:**
   ```bash
   kubectl apply -f manifests/
   ```

   Isso instalará o Portainer no seu cluster Kubernetes.

4. **Obtenha o IP do cluster:**
   ```bash
   k3d node list
   ```
   Anote o IP associado ao seu nó (normalmente `localhost`).

5. **Acesse o Portainer:**
   Abra o navegador e vá para [http://localhost:30777](http://localhost:30777).

   > **Nota:** Você acessará o Portainer pela porta 30777, conforme configurado no arquivo `service.yaml`.

6. **Verificar Portainer:**
   - Abra o navegador e acesse [http://localhost:30777](http://localhost:30777).
   - Siga as instruções do assistente de configuração do Portainer para se conectar ao cluster Kubernetes local.

     - **Usuário e Senha:**
       - Nome de usuário: `admin`
       - Senha: `admin` (ou sua senha escolhida)

   Se tudo estiver correto, você terá acesso visual ao seu cluster Kubernetes através do Portainer.

## Encerrando o Cluster

Para encerrar o cluster, execute o seguinte comando:

```bash
k3d cluster delete portainer-cluster
```

Isso removerá o cluster local e liberará os recursos.


## Referências
- [kubectl](https://kubernetes.io/)
- [Portainer](https://www.portainer.io/)
