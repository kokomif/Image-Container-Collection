This is a convenience image base written for the RunPod CPU-pod

---
At `Runpod-CPU` It includes:

- Ubuntu 20.04 base

- JupyterLab running on 8888

- SSH Daemon running on port 22

Image configuration via ENV variables:

**JUPYTER_PASSWORD**: This allows you to pre-configure the jupyter lab password that is used to auth. It will also start jupyter lab listening on port 8888

**PUBLIC_KEY**: This will set your public key into authorized_keys in ~/.ssh so you don't have to manually add it. It will also launch openssh daemon listening on port 22

---