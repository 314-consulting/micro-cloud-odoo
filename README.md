
---

# Micro Cloud Odoo

## Microk8s Odoo: Edge Computing Odoo

### Kubernetes Odoo
---

## [Project Kanban](https://github.com/orgs/GreenCloud-Consulting/projects/3)

## [Join Discord](https://discord.gg/y4kt5Vp2)

## [Issues](https://github.com/GreenCloud-Consulting/micro-cloud-odoo/issues)

## [Pull Requests](https://github.com/GreenCloud-Consulting/micro-cloud-odoo/pulls)


---

# Microk8s Odoo

## Table of Contents

- [About](#about)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Sponsors](#sponsors)
- [Authors](#authors)
- [Acknowledgments](#acknowledgement)
- [Instructions](#instructions)

## About <a name = "about"></a>

### All about Microk8s and Odoo.

Odoo Community is Open Source such as Microk8s.

We work with any Linux Distribution or other OS that support Microk8s as snap package or in other way.

We use cutting-edge technologies in Cloud Native Environment like Microk8s ( Kubernetes ).

We are focus on develop new way to manage and deploy Odoo environments in Public/Private Cloud.


## Roadmap <a name = "roadmap"></a>

### Project Priorites:

1. Incubate
2. Accelerate
3. Financial Support
4. Expand Communtiy
5. Be Singular in Odoo ecosystem


## Contributing <a name = "contributing"></a>

Freedom to contribute.

## Sponsor <a name = "sponsor"></a>

Be free to become a sponsor.

[Open Collective](https://opencollective.com/greencloud-consulting)

## Authors <a name = "authors"></a>

- [@JuanDCG](https://github.com/JuanDCG) - Original Idea & Initial Work


## 🎉 Acknowledgements <a name = "acknowledgement"></a>

- Hat tip to anyone whose code was used
- Inspiration
- References

## Instructions <a name = "instructions"></a>

### Running Odoo on MicroK8s

#### Install [MicroK8s](https://microk8s.io/)

`sudo snap install microk8s --classic --channel=1.22/stable`

#### Enable Plugins 

`sudo microk8s.enable rbac storage dashboard registry:size=20Gi dns ingress fluentd ha-cluster metrics-server portainer helm3`

`sudo microk8s.kubectl get all`

`sudo microk8s.status`


#### Kubernetes Dashboard

`token=$(microk8s kubectl -n kube-system get secret | grep default-token | cut -d " " -f1)`

`sudo microk8s kubectl -n kube-system describe secret $token`

`sudo microk8s kubectl port-forward -n kube-system service/kubernetes-dashboard 10443:443`

#### Fluentd

`sudo microk8s.kubectl port-forward -n kube-system service/kibana-logging 8181:5601`

`127.0.0.1:5601`

#### Portanier

`127.0.0.1:30777`

#### Restart MicroK8s

`sudo microk8s.stop`

`sudo microk8s.start`

`sudo microk8s.status`

#### Disable on start up

`sudo microk8s.disable`

#### Push images to private registry

`sudo docker build . -t localhost:32000/example:registry`

`sudo docker push localhost:32000/example`

#### Odoo Bitnami Helm3

[Info to customize](https://artifacthub.io/packages/helm/bitnami/odoo)

`sudo microk8s helm3 repo add bitnami https://charts.bitnami.com/bitnami`

`sudo microk8s helm3 install release-odoo bitnami/odoo`

##### Password

`password=$(microk8s kubectl get secret --namespace "default" release-odoo -o jsonpath="{.data.odoo-password}" | base64 --decode)`

`cat $password`


##### LoadBalancer IP: service/release-odoo 

`sudo microk8s.kubectl get all`

##### Endpoint IP:port

`sudo microk8s kubectl describe svc/release-odoo`
