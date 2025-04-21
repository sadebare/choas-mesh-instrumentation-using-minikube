# Chaos Mesh Experiments on Kubernetes

This project demonstrates how to use **[Chaos Mesh](https://chaos-mesh.org/)** to test the resilience and fault tolerance of a simple React-based application deployed on Kubernetes.

## 🔧 Setup

- [Kubernetes cluster](https://kubernetes.io/docs/tasks/tools/) set up
- [React app](./react-app/) is deployed in a custom namespace (`chaos-experiment`) with [yaml-file](./deployment-manifest/app.yaml)
- [Chaos Mesh](https://chaos-mesh.org/docs/quick-start/) installed and used for running various chaos experiments

## 🧪 Chaos Experiments

| Experiment     | Type         | Description |
|----------------|--------------|-------------|
| **[PodChaos](./chaos-mesh/podchaos.yaml)**   | `pod-kill`   | Kills all pods of the app and restarts them after 30s |
| **[HTTPChaos](./chaos-mesh/http-chaos.yaml)**  | `abort`      | Blocks HTTP GET requests for 10 minutes |
| **[NetworkChaos](./chaos-mesh/network-chaos.yaml)** | `bandwidth` | Simulates low network bandwidth (2 Mbps) |
| **[StressChaos](./chaos-mesh/stress-chaos.yaml)** | `cpu`        | Creates 80% CPU load on each container |
| **[TimeChaos](./chaos-mesh/time-chaos.yaml)**  | `time skew`  | Shifts system time by -10 minutes |

Each experiment was run using a custom YAML file inside the **[chaos-mesh/](./chaos-mesh/)** folder.

## 📸 Screenshots

Find all experiment results and UI screenshots in the **[screenshots/](./screenshots/)** folder.

## 🚀 Usage

To run any experiment, apply the YAML using:

```bash
kubectl apply -f chaos-mesh/<experiment-name>.yaml
