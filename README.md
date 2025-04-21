# Chaos Mesh Experiments on Kubernetes

This project demonstrates how to use **[Chaos Mesh](https://chaos-mesh.org/)** to test the resilience and fault tolerance of a simple React-based application deployed on Kubernetes.

## 🔧 Setup

- React app is deployed in a custom namespace (`chaos-experiment`)
- Exposed using a `NodePort` service or port-forward on service
- [Chaos Mesh](https://chaos-mesh.org/docs/quick-start/) installed and used for running various chaos experiments

## 🧪 Chaos Experiments

| Experiment     | Type         | Description |
|----------------|--------------|-------------|
| **PodChaos**   | `pod-kill`   | Kills all pods of the app and restarts them after 30s |
| **HTTPChaos**  | `abort`      | Blocks HTTP GET requests for 10 minutes |
| **NetworkChaos** | `bandwidth` | Simulates low network bandwidth (2 Mbps) |
| **StressChaos** | `cpu`        | Creates 80% CPU load on each container |
| **TimeChaos**  | `time skew`  | Shifts system time by -10 minutes |

Each experiment was run using a custom YAML file inside the `experiments/` folder.

## 📸 Screenshots

Find all experiment results and UI screenshots in the `screenshots/` folder.

## 🚀 Usage

To run any experiment, apply the YAML using:

```bash
kubectl apply -f experiments/<experiment-name>.yaml
