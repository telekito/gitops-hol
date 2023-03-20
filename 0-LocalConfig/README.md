# Environment setup

1. Chocolatey installation
    ```powershell   
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```

2. Az Cli installation
    ```powershell
    choco install azure-cli -y
    exit
    az upgrade
    ```

3. kubectl

    ```powershell
    az aks install-cli 
    ```

4. GIT
    ```powershell
    choco install git  -y
    ```

5. argocd cli
   
    ```powershell
    choco install argocd-cli  -y
    ```

6. openssl
    ```powershell
    choco install openssl -y
    ```

7. base64 
    ```powershell
    choco install base64 -y
    ```

<!-- 8. helm

```powershell
choco install kubernetes-helm
``` -->
8.  k9s

    ```powershell
    choco install k9s  -y
    ```
9. VSCode
    ```powershell
    choco install vscode  -y
    ```

<!-- az provider register -n 'Microsoft.Kubernetes -->
