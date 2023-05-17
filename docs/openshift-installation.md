# Installation in an OpenShift cluster using the OLM

This installation method is the recommended way for OpenShift users. **Note**: OpenShift version must be 4.2 or higher.

**Note: The `nginx-ingress-operator` supports `Basic Install` only - we do not support auto-updates. When you are installing the Operator using the OLM, the auto-update feature should be disabled to avoid breaking changes being auto-applied. In OpenShift, this can be done by setting the `Approval Strategy` to `Manual`. Please see the [Operator SDK docs](https://sdk.operatorframework.io/docs/overview/operator-capabilities/) for more details on the Operator Capability Levels.**

The NGINX Ingress Operator is a [RedHat certified Operator](https://connect.redhat.com/en/partner-with-us/red-hat-openshift-operator-certification).

1. In the OpenShift dashboard, click `Operators` > `Operator Hub` in the left menu and use the search box to type `nginx ingress`:
![alt text](./images/openshift1.png "Operators")
1. Click the `NGINX Ingress Operator` and click `Install`:
![alt text](./images/openshift2.png "NGINX Ingress Operator")
1. Click `Subscribe`:
![alt text](./images/openshift3.png "NGINX Ingress Operator Install")

OpenShift will install the NGINX Ingress Operator:

![alt text](./images/openshift4.png "NGINX Ingress Operator Subscribe")

Additional steps:

In order to deploy NGINX Ingress Controller instances into OpenShift environments, a new SCC is required to be created on the cluster which will be used to bind the specific required capabilities to the NGINX Ingress service account(s). To do so, please run the following command (assuming you are logged in with administrator access to the cluster):

`kubectl apply -f https://raw.githubusercontent.com/nginxinc/nginx-ingress-helm-operator/v1.4.1/resources/scc.yaml`

You can now deploy the NGINX Ingress Controller instances.
