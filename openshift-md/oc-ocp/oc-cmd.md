# OpenShift CLI (`oc`) Command Reference Guide

This guide provides a categorized, detailed reference to commonly used `oc` (OpenShift CLI) commands. Each entry includes usage, description, example, and any prerequisites.

---

## 🧑‍💼 Login and User Management

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc login` | Authenticate to an OpenShift cluster using a token or username/password. | `oc login --token=your-token`<br>`oc login --username=dev --password=pass` | OpenShift cluster access |
| `oc logout` | End the current authenticated session. | `oc logout` | Logged-in session |
| `oc whoami` | Display the current user context. | `oc whoami` | Logged-in session |
| `oc project` | Show or change the current project context. | `oc project myproject` | Logged-in session |
| `oc get projects` | List all projects the user has access to. | `oc get projects` | Logged-in session |

---

## 📦 Project Management

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc new-project` | Create a new OpenShift project (namespace) and set it as the current context. | `oc new-project dev-project` | Permission to create projects |
| `oc status` | Display a high-level overview of the current project. | `oc status` | Active project context |

---

## 📁 Resource Management

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc new-app` | Create a new application from source code, an image, or a template. | `oc new-app nodejs~https://github.com/sclorg/nodejs-ex` | Accessible Git repo or image stream |
| `oc new-build` | Set up a new build configuration. | `oc new-build https://github.com/sclorg/nodejs-ex` | Valid Git repo or Docker image |
| `oc get` | Retrieve one or more resources. | `oc get pods` | Resource must exist |
| `oc get svc` | List all services in the project. | `oc get svc` | - |
| `oc run` | Create and run a pod using a container image. | `oc run nginx --image=nginx` | Docker image |
| `oc expose` | Expose a service, route, or pod to internal or external traffic. | `oc expose svc/myservice` | Valid resource |
| `oc api-resources` | List all supported API resources. | `oc api-resources` | - |
| `oc explain` | Show detailed documentation of a resource and its fields. | `oc explain pods` | - |
| `oc replace -f` | Replace a resource with the configuration in a file. | `oc replace -f pod.yaml` | YAML must define the resource |
| `oc delete -f` | Delete resource(s) specified in a file. | `oc delete -f pod.yaml` | Valid resource file |
| `oc edit` | Edit a resource using the default text editor. | `oc edit svc/myservice` | Resource must exist |
| `oc describe` | Display detailed information about a resource. | `oc describe pod/mypod` | Resource must exist |
| `oc apply -f` | Apply configuration from a YAML or JSON file. | `oc apply -f deployment.yaml` | Valid file with resource definition |
| `oc create -f` | Create a new resource from a file. | `oc create -f configmap.yaml` | Valid resource file |
| `oc label` | Add or modify labels on resources. | `oc label pod/mypod env=dev` | Resource must exist |
| `oc annotate` | Add or change annotations on resources. | `oc annotate pod/mypod description="Test pod"` | Resource must exist |

---

## ⚙️ Operational Commands

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc logs` | View logs from a specific container in a pod. | `oc logs mypod` | Pod must be running |
| `oc rsh` | Start an interactive shell session inside a pod. | `oc rsh mypod` | Pod must be running |
| `oc rsync` | Synchronize files between a local directory and a container. | `oc rsync ./app mypod:/app` | Pod must exist |
| `oc exec` | Execute a command inside a container. | `oc exec mypod -- ls /app` | Pod must be running |
| `oc idle` | Scale down a resource to zero replicas and disable its service. | `oc idle svc/myservice` | Service must exist |

---

## 🔧 Cluster and Admin Commands

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc adm` | Access administrative subcommands. | `oc adm top nodes` | Cluster-admin |
| `oc adm must-gather` | Gather cluster diagnostic data. | `oc adm must-gather` | Cluster-admin |
| `oc adm inspect` | Collect diagnostic data for a specific resource. | `oc adm inspect nodes` | - |
| `oc adm policy` | Manage access policies and role bindings. | `oc adm policy add-role-to-user edit user1` | Admin access |
| `oc adm cordon` | Mark a node as unschedulable. | `oc adm cordon node1` | Node must exist |
| `oc adm uncordon` | Mark a node as schedulable. | `oc adm uncordon node1` | Node must exist |
| `oc adm drain` | Evacuate all pods from a node. | `oc adm drain node1` | Node must exist |
| `oc adm upgrade` | Upgrade the OpenShift cluster. | `oc adm upgrade` | Cluster-admin |
| `oc adm top` | Show current resource usage statistics. | `oc adm top pods` | Metrics server must be installed |

---

## ⚙️ Set and Patch Commands

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc patch` | Apply a partial update to a resource. | `oc patch deployment mydep -p '{"spec":{"replicas":2}}' --type=merge` | Valid patch format |
| `oc extract` | Download secret or configmap contents to the local file system. | `oc extract secret/mysecret --to=./` | Resource must exist |
| `oc set probe` | Add or update liveness/readiness probes. | `oc set probe deployment/myapp --liveness ...` | Deployment must exist |
| `oc set volumes` | Add or configure volumes for pod templates. | `oc set volume deployment/myapp --add --name=vol1 --mount-path=/data` | - |
| `oc set build-hook` | Configure build hooks. | `oc set build-hook bc/myapp --post-commit --script='echo Hello'` | BuildConfig |
| `oc set env` | Manage environment variables for a deployment. | `oc set env deployment/myapp ENV=prod` | Resource must exist |
| `oc set image` | Update the container image. | `oc set image deployment/myapp app=image:v2` | Deployment must exist |
| `oc set triggers` | Configure deployment triggers. | `oc set triggers dc/myapp --from-image ...` | DeploymentConfig |
| `oc set serviceaccount` | Associate a service account to a deployment. | `oc set serviceaccount dc/myapp myaccount` | Valid account and DC |
| `oc set route-backends` | Adjust route weight to multiple services. | `oc set route-backends myroute serviceA=60 serviceB=40` | Valid route and services |

---

## 🚀 Build & Deploy Commands

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc rollout` | Manage deployment rollout. | `oc rollout status deployment/myapp` | Deployment must exist |
| `oc rollout latest` | Trigger a new rollout. | `oc rollout latest dc/myapp` | DeploymentConfig |
| `oc rollout undo` | Roll back to the previous version. | `oc rollout undo deployment/myapp` | - |
| `oc rollout history` | Show rollout history. | `oc rollout history deployment/myapp` | - |
| `oc rollout status` | Show rollout progress. | `oc rollout status deployment/myapp` | - |
| `oc tag` | Tag an image into an image stream. | `oc tag myimage:latest myimage:v2` | Image must exist |
| `oc rollback` | Rollback a deployment or DC. | `oc rollback myapp` | Previous version must exist |
| `oc start-build` | Manually trigger a build. | `oc start-build myapp` | BuildConfig must exist |
| `oc cancel-build` | Cancel an ongoing build. | `oc cancel-build myapp-1` | Build must be in progress |
| `oc import-image` | Import an image from an external registry. | `oc import-image nginx` | Network access required |
| `oc scale` | Change number of pod replicas. | `oc scale deployment/myapp --replicas=3` | Deployment must exist |
| `oc debug` | Create a temporary debug pod. | `oc debug node/mynode` | Resource must exist |

---

## 🧬 JSONPath Queries

| Command | Description | Example | Prerequisites |
|--------|-------------|---------|----------------|
| `oc get -o jsonpath=` | Query JSON output using JSONPath syntax. | `oc get pods -o jsonpath='{.items[*].metadata.name}'` | JSONPath knowledge |

---

> ✨ **Note:** All commands assume that `oc` is installed and the user is authenticated to a valid OpenShift cluster with the required permissions.

