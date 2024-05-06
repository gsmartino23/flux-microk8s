# Demo de Flux con Microk8s en Mac

Este repositorio contiene una demostración de cómo usar Flux con Microk8s en una Mac.

## Prerrequisitos

Antes de comenzar, asegúrate de tener lo siguiente instalado en tu máquina:

1. **Microk8s**: MicroK8s es un pequeño, rápido, Kubernetes de un solo paquete para desarrolladores, IoT y Edge.

   Instalación con Homebrew:
   ```bash
   brew install ubuntu/microk8s/microk8s
   microk8s install
   ```

2. **Flux**: Flux es una herramienta para mantener el estado del clúster de Kubernetes en sincronía con los archivos de configuración en Git.

   Instalación con Homebrew:
   ```bash
   brew install fluxcd/tap/flux
   ```

3. **kubectl**: kubectl es una herramienta de línea de comandos que permite ejecutar comandos contra clústeres de Kubernetes.

   Instalación con Homebrew:
   ```bash
   brew install kubectl 
   ```

4. **Credenciales de GitHub**: Necesitarás un token de acceso personal de GitHub para que Flux pueda interactuar con tus repositorios. Sigue las instrucciones en la [documentación oficial de GitHub](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) para crear uno.

5. **Un clúster de Kubernetes**: Microk8s instalará un clúster de Kubernetes en tu máquina local. Asegúrate de que esté en ejecución con el comando:
   ```bash
   microk8s status --wait-ready
   ```

## Instalación

Una vez que hayas instalado los prerrequisitos, puedes proceder con la instalación de Flux en tu clúster de Kubernetes.

1. Asegúrate de que tu clúster de Kubernetes esté en ejecución:
   ```bash
   microk8s status --wait-ready
   ```

2. Instala Flux en el clúster:
   ```bash
   flux bootstrap github --owner=<tu nombre de usuario de GitHub> --repository=<tu repositorio> --branch=main --path=./clusters/my-cluster --personal
   ```

3. Verifica que Flux esté en ejecución:
   ```bash
   flux check
   ```
