# lilwang_iot

GitOps manifests watched by Argo CD for the
[Inception-of-Things](https://github.com/liliane0128/Inception_of_things) Part 3
exercise (42 school). This repo holds nothing but what gets deployed —
the cluster bootstrap (Vagrant, install script, Argo CD's own `Application`
resource) lives in the main project repo.

## manifests/

Deploys [wil42/playground](https://hub.docker.com/r/wil42/playground) into
the `dev` namespace.

- `deployment.yaml` — the image tag here is the whole point of the exercise:
  edit it (`v1` ↔ `v2`), commit, push, and Argo CD's automated + selfHeal
  sync policy rolls it out with no manual `kubectl` involved.
- `service.yaml` — `type: LoadBalancer`, so k3d's built-in load balancer
  picks it up and the app is reachable at `localhost:8888` on the VM.
