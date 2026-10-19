# dockerhub-datascience-mlops-kernels

![JupyterLab Kernels](https://raw.githubusercontent.com/JorgeCardona/dockerhub-datascience-mlops-kernels/refs/heads/main/images/kernels.png)

**English** | Español

---

# English

## Overview

**dockerhub-datascience-mlops-kernels** is a multi-language Docker environment built for Data Science, Machine Learning, MLOps, scientific computing, software development, and blockchain engineering.

Based on Python 3.14, it provides a preconfigured JupyterLab workspace with multiple programming languages, interactive kernels, development tools, and blockchain frameworks.

The goal is to provide a unified environment where developers, researchers, data scientists, and engineers can work with different technologies without configuring each language and runtime manually.

## Supported Languages and Kernels

| Language | Runtime / Kernel | Main Applications |
| --- | --- | --- |
| Python 3.14 | IPython / ipykernel | Data Science, Machine Learning, AI, and MLOps |
| C++ | jupyter-cpp-kernel | Systems programming and numerical computing |
| Java 25 | IJava | Enterprise development and JVM applications |
| Scala | Almond | Big Data and Apache Spark development |
| R 4.5 | IRkernel | Statistics and data analysis |
| Julia | IJulia | Scientific and numerical computing |
| Kotlin | Kotlin Jupyter Kernel | JVM development and data processing |
| Elixir | Custom Jupyter kernel | Functional and concurrent programming |
| MATLAB / Octave | octave\_kernel | Numerical computing and engineering |
| JavaScript | IJavascript | Node.js development and scripting |
| JavaScript / TypeScript | Deno Jupyter | Modern JavaScript and TypeScript |
| Go | Gophernotes | Backend and systems development |
| Rust | evcxr\_jupyter | Systems programming and performance |
| Ruby | IRuby | Scripting and application development |
| Bash | bash\_kernel | Shell scripting and automation |
| C# | .NET Interactive | .NET development |
| F# | .NET Interactive | Functional programming on .NET |
| Solidity | Custom Solidity Jupyter kernel | Smart contract compilation and development |

> **Compatibility:** Available runtimes, language versions, and kernel capabilities depend on the installed packages and the version of the Docker image.

## Blockchain Development Environment

The image includes a blockchain development toolchain for compiling, testing, deploying, and interacting with Solidity smart contracts.

### Included Tools

- **Solidity (****`solc`****)** — Compiles smart contracts and generates ABI and bytecode artifacts.
- **Solidity Jupyter Kernel** — Compiles Solidity source code directly in JupyterLab notebook cells.
- **Ganache** — Runs a local Ethereum-compatible blockchain for development and testing.
- **Hardhat** — Provides smart contract development, automated testing, deployment, and debugging.
- **Ethers.js** — JavaScript library for interacting with Ethereum-compatible blockchains.
- **Foundry** — Smart contract development toolkit:
  - `forge`: Build, test, and deploy smart contracts.
  - `cast`: Interact with blockchain RPC endpoints and smart contracts.
  - `anvil`: Run a local Ethereum development node.
  - `chisel`: Interactive Solidity command-line environment.

### Solidity in JupyterLab

The custom Solidity kernel compiles source code entered directly into notebook cells and displays compiler diagnostics and generated artifacts, including ABI and bytecode.

Example:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract HelloWorld {
    string public message = "Hello, Solidity!";

    function setMessage(string memory newMessage) public {
        message = newMessage;
    }
}
```

The kernel handles compilation. Deploying contracts, executing transactions, and interacting with deployed contracts require a blockchain node and suitable tools such as Ganache, Hardhat, or Anvil.

### Verify Blockchain Tools

Run the following commands inside the container:

```
solc --version
ganache --version

cd /opt/solidity-workspace

./node_modules/.bin/hardhat --version
npm ls hardhat @nomicfoundation/hardhat-ethers ethers

forge --version
cast --version
anvil --version
chisel --version
```

Foundry commands require a successful Foundry installation and the appropriate executable paths. Hardhat commands should be run from the project directory.

### Security Considerations

- Never use development private keys or test accounts with real funds.
- Do not expose blockchain RPC endpoints publicly without appropriate access controls.
- Keep production credentials and private keys outside the Docker image.
- Use a secrets management solution for production deployments.
- Treat development blockchain accounts and their private keys as disposable.

## Key Features

- **Multi-language JupyterLab:** Work with different programming languages from a single interface.
- **Data Science and MLOps:** Python-based analytical and machine learning workflows.
- **Blockchain development:** Solidity compilation and Ethereum development tools.
- **Git integration:** Includes the `jupyterlab-git` extension.
- **Containerized environment:** A reproducible workspace based on Docker.
- **Persistent notebooks:** Uses `/notebooks` as the default working directory.
- **Custom kernels:** Additional kernel configurations for languages requiring specialized setup.

## Quick Start

### 1\. Pull the Docker Image

```
docker pull jorgecardona/datascience-mlops-kernels:latest
```

### 2\. Run the Container

```
docker run -d \
  --name datascience-kernels \
  -p 8888:8888 \
  -v "$(pwd)/notebooks:/notebooks" \
  jorgecardona/datascience-mlops-kernels:latest
```

### 3\. Open JupyterLab

Navigate to:

```
http://localhost:8888
```

The example assumes JupyterLab starts on port `8888`. Configure authentication according to your deployment requirements.

### Windows PowerShell

```
New-Item -ItemType Directory -Force .\notebooks

docker run -d `
  --name datascience-kernels `
  -p 8888:8888 `
  -v "${PWD}/notebooks:/notebooks" `
  jorgecardona/datascience-mlops-kernels:latest
```

## Build the Docker Image

Clone the repository:

```
git clone https://github.com/JorgeCardona/dockerhub-datascience-mlops-kernels.git
cd dockerhub-datascience-mlops-kernels
```

Build the image:

```
docker build \
  --tag jorgecardona/datascience-mlops-kernels:latest .
```

Push the image to Docker Hub:

```
docker push jorgecardona/datascience-mlops-kernels:latest
```

## Verify the Installation

### List Jupyter Kernels

```
jupyter kernelspec list
```

### Check Language Runtimes

```
python --version
java --version
R --version
julia --version
go version
rustc --version
node --version
deno --version
dotnet --version
```

### Check Blockchain Tools

```
solc --version
ganache --version
forge --version
cast --version
anvil --version
chisel --version
```

Some commands require a particular working directory or an executable available in `PATH`.

## Workspace and Persistent Storage

The default working directory is:

```
/notebooks
```

Mount a local directory to preserve notebooks and project files when the container is removed or recreated.

## Network Ports

| Port | Purpose |
| --- | --- |
| `8888` | JupyterLab |
| `8545` | Typical Ethereum JSON-RPC endpoint when a blockchain node is running and configured |

Additional ports can be published for services explicitly started inside the container.

## Repository and Distribution

- **GitHub:** https://github.com/JorgeCardona/dockerhub-datascience-mlops-kernels
- **Docker Hub:** [https://hub.docker.com/r/jorgecardona/datascience-mlops-kernels](<https://hub.docker.com/r/jorgecardona/datascience-mlops-kernels>)

## Disclaimer

This project integrates third-party software into a containerized development environment. Each language runtime, kernel, compiler, and framework is maintained by its respective project.

Available features and compatibility depend on the image version and installed dependencies.

---

# Español

## Descripción general

**dockerhub-datascience-mlops-kernels** es un entorno Docker multilenguaje diseñado para Ciencia de Datos, Machine Learning, MLOps, computación científica, desarrollo de software e ingeniería blockchain.

Basado en Python 3.14, proporciona un entorno JupyterLab preconfigurado con múltiples lenguajes de programación, kernels interactivos, herramientas de desarrollo y frameworks para blockchain.

El objetivo es ofrecer un espacio de trabajo unificado donde desarrolladores, investigadores, científicos de datos e ingenieros puedan trabajar con distintas tecnologías sin tener que configurar manualmente cada lenguaje y entorno de ejecución.

## Lenguajes y kernels soportados

| Lenguaje | Runtime / Kernel | Aplicaciones principales |
| --- | --- | --- |
| Python 3.14 | IPython / ipykernel | Ciencia de Datos, Machine Learning, IA y MLOps |
| C++ | jupyter-cpp-kernel | Programación de sistemas y computación numérica |
| Java 25 | IJava | Desarrollo empresarial y aplicaciones JVM |
| Scala | Almond | Big Data y desarrollo con Apache Spark |
| R 4.5 | IRkernel | Estadística y análisis de datos |
| Julia | IJulia | Computación científica y numérica |
| Kotlin | Kotlin Jupyter Kernel | Desarrollo JVM y procesamiento de datos |
| Elixir | Kernel Jupyter personalizado | Programación funcional y concurrente |
| MATLAB / Octave | octave\_kernel | Computación numérica e ingeniería |
| JavaScript | IJavascript | Desarrollo con Node.js y scripting |
| JavaScript / TypeScript | Deno Jupyter | Desarrollo moderno con JavaScript y TypeScript |
| Go | Gophernotes | Desarrollo backend y de sistemas |
| Rust | evcxr\_jupyter | Programación de sistemas y alto rendimiento |
| Ruby | IRuby | Automatización y desarrollo de aplicaciones |
| Bash | bash\_kernel | Automatización y scripting de shell |
| C# | .NET Interactive | Desarrollo sobre .NET |
| F# | .NET Interactive | Programación funcional sobre .NET |
| Solidity | Kernel Jupyter personalizado para Solidity | Compilación y desarrollo de contratos inteligentes |

> **Compatibilidad:** Los runtimes, las versiones de los lenguajes y las capacidades de cada kernel dependen de los paquetes instalados y de la versión de la imagen Docker.

## Entorno de desarrollo blockchain

La imagen incorpora herramientas para compilar, probar, desplegar e interactuar con contratos inteligentes escritos en Solidity.

### Herramientas incluidas

- **Solidity (****`solc`****)** — Compila contratos inteligentes y genera los artefactos ABI y bytecode.
- **Kernel Jupyter de Solidity** — Permite compilar código Solidity directamente en las celdas de los notebooks de JupyterLab.
- **Ganache** — Ejecuta una blockchain local compatible con Ethereum para desarrollo y pruebas.
- **Hardhat** — Facilita el desarrollo, las pruebas automatizadas, el despliegue y la depuración de contratos inteligentes.
- **Ethers.js** — Biblioteca JavaScript para interactuar con blockchains compatibles con Ethereum.
- **Foundry** — Kit de herramientas para desarrollo de contratos inteligentes:
  - `forge`: Compilar, probar y desplegar contratos inteligentes.
  - `cast`: Interactuar con endpoints RPC y contratos inteligentes.
  - `anvil`: Ejecutar un nodo local de desarrollo compatible con Ethereum.
  - `chisel`: Entorno interactivo de Solidity desde la línea de comandos.

### Solidity en JupyterLab

El kernel personalizado de Solidity compila el código introducido directamente en las celdas del notebook y muestra los diagnósticos del compilador y los artefactos generados, incluidos ABI y bytecode.

Ejemplo:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract HolaMundo {
    string public mensaje = "¡Hola, Solidity!";

    function cambiarMensaje(string memory nuevoMensaje) public {
        mensaje = nuevoMensaje;
    }
}
```

El kernel se encarga de la compilación. Para desplegar contratos, ejecutar transacciones e interactuar con contratos desplegados se necesita un nodo blockchain y herramientas adecuadas, como Ganache, Hardhat o Anvil.

### Validar las herramientas blockchain

Ejecuta estos comandos dentro del contenedor:

```
solc --version
ganache --version

cd /opt/solidity-workspace

./node_modules/.bin/hardhat --version
npm ls hardhat @nomicfoundation/hardhat-ethers ethers

forge --version
cast --version
anvil --version
chisel --version
```

Los comandos de Foundry requieren que la instalación haya finalizado correctamente y que los ejecutables estén disponibles en `PATH`. Los comandos de Hardhat deben ejecutarse desde el directorio del proyecto.

### Consideraciones de seguridad

- Nunca utilices claves privadas de desarrollo ni cuentas de prueba con fondos reales.
- No expongas públicamente endpoints RPC sin controles de acceso adecuados.
- Mantén las credenciales de producción y las claves privadas fuera de la imagen Docker.
- Utiliza un sistema de gestión de secretos para despliegues de producción.
- Considera desechables las cuentas blockchain de desarrollo y sus claves privadas.

## Características principales

- **JupyterLab multilenguaje:** Trabaja con diferentes lenguajes de programación desde una única interfaz.
- **Ciencia de Datos y MLOps:** Entorno basado en Python para análisis de datos y flujos de trabajo de Machine Learning.
- **Desarrollo blockchain:** Compilación de Solidity y herramientas para el ecosistema Ethereum.
- **Integración con Git:** Incluye la extensión `jupyterlab-git`.
- **Entorno contenerizado:** Espacio de trabajo reproducible mediante Docker.
- **Notebooks persistentes:** Utiliza `/notebooks` como directorio de trabajo predeterminado.
- **Kernels personalizados:** Configuraciones adicionales para lenguajes que requieren una instalación especializada.

## Inicio rápido

### 1\. Descargar la imagen Docker

```
docker pull jorgecardona/datascience-mlops-kernels:latest
```

### 2\. Ejecutar el contenedor

```
docker run -d \
  --name datascience-kernels \
  -p 8888:8888 \
  -v "$(pwd)/notebooks:/notebooks" \
  jorgecardona/datascience-mlops-kernels:latest
```

### 3\. Abrir JupyterLab

Accede desde tu navegador a:

```
http://localhost:8888
```

Este ejemplo supone que JupyterLab se inicia en el puerto `8888`. Configura la autenticación de acuerdo con los requisitos de tu despliegue.

### Windows PowerShell

```
New-Item -ItemType Directory -Force .\notebooks

docker run -d `
  --name datascience-kernels `
  -p 8888:8888 `
  -v "${PWD}/notebooks:/notebooks" `
  jorgecardona/datascience-mlops-kernels:latest
```

## Construir la imagen Docker

Clona el repositorio:

```
git clone https://github.com/JorgeCardona/dockerhub-datascience-mlops-kernels.git
cd dockerhub-datascience-mlops-kernels
```

Construye la imagen:

```
docker build \
  --tag jorgecardona/datascience-mlops-kernels:latest .
```

Publica la imagen en Docker Hub:

```
docker push jorgecardona/datascience-mlops-kernels:latest
```

## Validar la instalación

### Listar los kernels de Jupyter

```
jupyter kernelspec list
```

### Comprobar los runtimes de los lenguajes

```
python --version
java --version
R --version
julia --version
go version
rustc --version
node --version
deno --version
dotnet --version
```

### Comprobar las herramientas blockchain

```
solc --version
ganache --version
forge --version
cast --version
anvil --version
chisel --version
```

Algunos comandos requieren ejecutarse desde un directorio concreto o tener los ejecutables disponibles en `PATH`.

## Espacio de trabajo y almacenamiento persistente

El directorio de trabajo predeterminado es:

```
/notebooks
```

Vincula una carpeta local para conservar notebooks y archivos del proyecto aunque elimines o recrees el contenedor.

## Puertos de red

| Puerto | Uso |
| --- | --- |
| `8888` | JupyterLab |
| `8545` | Endpoint JSON-RPC habitual de Ethereum cuando hay un nodo blockchain ejecutándose y configurado |

Puedes publicar puertos adicionales para los servicios que inicies explícitamente dentro del contenedor.

## Repositorio y distribución

- **GitHub:** https://github.com/JorgeCardona/dockerhub-datascience-mlops-kernels
- **Docker Hub:** [https://hub.docker.com/r/jorgecardona/datascience-mlops-kernels](<https://hub.docker.com/r/jorgecardona/datascience-mlops-kernels>)

## Aviso legal

Este proyecto integra software de terceros en un entorno de desarrollo contenerizado. Cada runtime, kernel, compilador y framework es mantenido por su respectivo proyecto.

Las funcionalidades disponibles y la compatibilidad dependen de la versión de la imagen y de las dependencias instaladas.

Importante: he documentado las herramientas que aparecen en tu Dockerfile. Antes de publicar, verifica que todos los kernels y las herramientas de Foundry se instalen correctamente en la imagen final; que aparezcan en el README no garantiza que estén disponibles en todas las versiones.