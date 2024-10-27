# 安装
```shell
KUBECTL_VERSION=v1.31.0
curl -LO "https://dl.k8s.io/release/$KUBECTL_VERSION/bin/linux/amd64/kubectl" 
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/ 
```

# 配置自动补全
```shell
cat <<'EOF' >> ~/.bashrc
alias k='kubectl'
alias kctx='k config get-contexts'
source <(kubectl completion bash)
source <(kubectl completion bash | sed s/kubectl/k/g)

_kcd_complete()
{
    local cur="${COMP_WORDS[COMP_CWORD]}"
    COMPREPLY=( $(kubectl get ns --no-headers -o custom-columns=:metadata.name | grep "^${cur}") )
}

function kcd()
{
    local ns="default"
    [ -n "$1" ] && ns="$1"
    kubectl config set-context "$(kubectl config current-context)" --namespace="$ns"
}

complete -F _kcd_complete kcd


_kcc_complete() {
    local cur="${COMP_WORDS[COMP_CWORD]}"
    COMPREPLY=( $(kubectl config get-contexts --no-headers -o name | grep "^${cur}") )
}

kcc() {
    if [ -z "$1" ]; then
        echo "Usage: kcc <context>"
    else
        kubectl config use-context "$1"
    fi
}

complete -F _kcc_complete kcc
EOF

source ~/.bashrc
```

# 使用
```shell
# kcd [namespace]
kcd ku<tab>
k get po
kcd  d<tab>
```