## 安装及使用

### 1. 官方安装文档
    - [安装](https://kind.sigs.k8s.io/docs/user/quick-start/)
    - [配置](https://kind.sigs.k8s.io/docs/user/configuration/)

### 2. 快速安装
   * On Linux For AMD64 / x86_64
      ```shell
      KIND_VERSION=v0.24.0
      [ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-amd64
      chmod +x ./kind
      sudo mv ./kind /usr/local/bin/kind
      ```
   * On Linux For ARM64
      ```shell
      KIND_VERSION=v0.24.0
      [ $(uname -m) = arm64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-arm64
      chmod +x ./kind
      sudo mv ./kind /usr/local/bin/kind
      ```
### 3. 自动补全
   ```shell
   echo 'source <(kind completion bash)' >> ~/.bashrc && \
   source ~/.bashrc

   # or
   kind completion bash | sudo tee /etc/bash_completion.d/kind > /dev/null
   source /etc/bash_completion.d/kind
  ```
### 4. 安装 k8s:
   * 创建单节点集群
   ```shell
  # 安装最新版本
  curl -Lo ./kind-config-single-node.yaml https://raw.githubusercontent.com/ace-zhaoy/k8s-in-action/master/Kind/kind-config-single-node.yaml
  kind create cluster --config=kind-config-single-node.yaml
  
  # 安装指定版本
  curl -Lo ./kind-config-single-node.yaml https://raw.githubusercontent.com/ace-zhaoy/k8s-in-action/master/Kind/kind-config-single-node.yaml
  kind create cluster --image=kindest/node:v1.28.13 --config=kind-config-single-node.yaml
   ```
镜像版本可以在 [hub.docker.com](https://hub.docker.com/r/kindest/node/tags) 查看

   * 创建多节点集群
   ```shell
  curl -Lo ./kind-config-multi-node.yaml https://raw.githubusercontent.com/ace-zhaoy/k8s-in-action/master/Kind/kind-config-multi-node.yaml
  kind create cluster --config=kind-config-multi-node.yaml
   ```