# Repository configuration

1. Create and initialize the repository for the lab in GitHub

2. Create the ssh keys

    ```powershell
    ssh-keygen -t ed25519 -C '<your github email address>'
    ```

3. Go to https://github.com/\<github account\>/\<repository\>/settings/keys and click "Add deploy key" and "Allow write access"

4. Open the public key with a text editor and copy it

5. Clone the repository

    ```powershell
    git clone <repository url>
    ```

6. Go to the repository folder and open vs code
    ```powershell
    cd <folder>
    code .
    ```

7. Create the folder structure

   1. OPA Gatekeeper
        ```powershell
        mkdir -p cluster/global/gatekeeper-system
        echo "" > cluster/global/gatekeeper-system/.gitkeep
        mkdir -p cluster/global/policies
        echo "" > cluster/global/policies/.gitkeep
        ```

   2. Create demo app (the folder represents the kubernetes namespace)
        ```powershell
        mkdir -p cluster/namespaces/demo-app/
        ```

8. Add the kubernetes manifest demo.yaml (nginx) in the created folder
    ```yaml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: hello-world
      labels:
        app: hello-world
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: hello-world
      template:
        metadata:
          labels:
            app: hello-world
        spec:
          containers:
          - name: nginx
            image: nginx:1.21.1
            ports:
            - containerPort: 80
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: hello-world
    spec:
      type: LoadBalancer
      ports:
      - port: 80
      selector:
        app: hello-world
    ```

9. Add the configuration for GIT (if needed)
    ```powershell
    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"
    ```

10. Commit and push the changes to the repository
    ```powershell
    git add cluster
    git commit -m "layout creation"
    git push
    ```

11. Create the branches for the needed environments (the master branch is our clients branch for gitops deployment)
    1.  Development
    ```powershell
    git checkout -b dev
    git push --set-upstream origin dev
    ```    
