# Introduction
This a postgresql helm chart that would be integrated with zabbix solution.

# Getting Started
To run this chart, follow these steps:
1. Make sure that you have helm running in your host.
2. Run the following command to pull ``postgresql`` helm chart dependencies:
    ```shell 
   helm dependency update .
    ```
3. Create a secret that will hold the database passwords. The secret object should look like this (change the data values):
    ```yaml
    apiVersion: v1
    kind: Secret
    metadata:
      name: postgresql-secret
    data:
      postgresql-postgres-password: "UG9zdGdSZXMyTWU="
      postgresql-password: "UG9zdGdSZXMyWmFiYml4"
    ```
4. For dev purposes, you can comment the files under templates' folder, as well as the ``postgresql.persistence`` part
    in the ``values.yaml`` file.
5. Create a database namespace that will hold the resources of this chart by running the following command:
```shell
kubectl create ns database
```
6. Finally, install the chart by running the following command:
```shell
helm install postgresql postgresql-helm-chart -f postgresql-helm-chart/values.yaml -n database
```
