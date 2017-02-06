# Hands on with Kubernetes Workshops

A demo repo for running the Kismatic Enterprise Toolkit on Digital Ocean

The following repository will create you a Kubernetes cluster using the following:

1. The underlying Infrastructure using Digital Ocean
2. Infrastructure creation using Terraform
3. Cluster provisoning using the Kismatic Enterprise Toolkit (KET)

## Prerequisities

### 1. Terraform

Before using this repository you will need to download and install [Terraform](https://www.terraform.io/)

This can be downloaded from [here](https://www.terraform.io/downloads.html)

Download and place the Terraform binary in your preferred location, then tweak the command below and execute it:

```
$ PATH=/usr/local/terraform/bin:<terraform location>:$PATH
```

### 2. Digital Ocean account

You will also require an account on [https://www.digitalocean.com/](https://www.digitalocean.com/)

## Usage

### 1. Create Infrastructure

Before executing Terraform you need to obtain your Digital Ocean token [here](https://cloud.digitalocean.com/settings/api/tokens)

To see the changes which are going to be made execute the following commands:

```
$ export TF_VAR_digital_ocean_token=
$ make plan
```

To apply the changes execute the following commands:

```
$ export TF_VAR_digital_ocean_token=
$ make apply
```

### 2. Provision Kubernetes cluster

To provision the Kubernetes cluster execute the following command:

```
$ make get-kismatic
```

Now update the `kismatic-cluster.yaml` to have the correct IP addresses, once you have filled that in execute:

```
$ make provision-cluster
```

Note: You can specify which version of KET by updating the `KISMATIC_VERSION` variable in the Makefile.