# Toolbox Image (Standalone Build Repo)

Detta repo bygger och publicerar en verktygscontainer med nano, net-tools, iproute2, ping, dnsutils, curl, tcpdump, mtr, nmap, jq, iperf3 m.m.

## Snabbstart (lokalt)
```bash
make build print
make push-latest   # kräver docker login mot ditt registry
```

## GitHub Container Registry (GHCR)
1. Skapa repo på GitHub och pusha denna kod.
2. Aktivera GitHub Actions.
3. Vid push till `main` bygger workflow `build-push.yml` och publicerar:
   - `ghcr.io/<owner>/toolbox:latest`
   - `ghcr.io/<owner>/toolbox:<git-sha>`

## Använd i ditt GitOps-repo
Peka din Deployment till publicerade imagen, t.ex.
```yaml
containers:
  - name: toolbox
    image: ghcr.io/<owner>/toolbox:latest
    command: ["bash","-lc","sleep infinity"]
    tty: true
    stdin: true
```

> Detta repo innehåller **endast** byggdelen. Ditt GitOps-repo behåller kustomize/overlays m.m.
