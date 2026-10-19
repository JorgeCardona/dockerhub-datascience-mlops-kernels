# dockerhub-datascience-mlops-kernels

![JupyterLab Kernels](https://raw.githubusercontent.com/JorgeCardona/dockerhub-datascience-mlops-kernels/refs/heads/main/images/kernels.png)

**English** | Español

---

# English

## Overview

A multi-language Docker environment for Data Science, Machine Learning, MLOps, scientific computing, software development, and blockchain engineering.

Built on Python 3.14, this image integrates multiple programming languages, Jupyter kernels, development frameworks, and blockchain tools into a unified JupyterLab environment.

The image is designed to provide a reproducible development workspace. Versions explicitly pinned in the Dockerfile are documented below. Components installed without an explicit version may change between image builds.

## Software Stack and Versions

### Base Environment

| Component | Version | Installation / Notes |
| --- | --- | --- |
| Python | `3.14.7` | Base Docker image: `python:3.14.7` |
| JupyterLab | Latest available at build time | Installed using `pip install --upgrade jupyterlab` |
| IPython Kernel | Latest compatible at build time | Installed through `ipykernel` |
| CMake | Distribution-provided | Installed through APT |
| GNU C++ compiler | Distribution-provided | Installed through `g++` and `build-essential` |

### Programming Languages and Runtimes

| Language / Runtime | Version | Kernel / Implementation |
| --- | --- | --- |
| Python | `3.14.7` | IPython / ipykernel |
| Java | JDK `25` | IJava `1.3.0` |
| Scala | `2.13.18` | Almond `0.14.5` |
| R | `4.5.0` package revision `-3` requested | IRkernel; version not pinned |
| Go | Distribution-provided | Gophernotes `0.7.5` |
| Rust | `1.98.1` requested | evcxr\_jupyter; version not pinned |
| Julia | `1.13.0` | IJulia; package version not pinned |
| Node.js | `20.19.2` | IJavascript; version not pinned |
| Deno | Latest available from the installer | Deno Jupyter |
| Kotlin | Not explicitly pinned | Kotlin Jupyter Kernel |
| Elixir | Distribution-provided | Custom Jupyter kernel |
| Ruby | Distribution-provided | IRuby `0.8.3` |
| C++ | Distribution compiler | jupyter-cpp-kernel; package version not pinned |
| MATLAB-compatible environment | GNU Octave `9.4.0` requested | octave\_kernel `1.1.1` |
| Bash | Distribution shell | bash\_kernel; package version not pinned |
| C# | .NET SDK `10.0` channel | .NET Interactive; tool version not pinned |
| F# | .NET SDK `10.0` channel | .NET Interactive; tool version not pinned |
| Solidity | `solc` npm package `0.8.37` in the reported build | Custom Solidity Jupyter kernel `1.0` |
| JavaScript | Node.js `20.19.2` | IJavascript |
| TypeScript / JavaScript | Deno installer version | Deno Jupyter |

**Version policy:** A requested version is not necessarily proof of the version ultimately installed. APT package availability, upstream installers, package resolution, and compatibility constraints can affect the final result. The Docker build should verify the installed version.

### Blockchain Development Stack

| Tool | Version / Configuration | Purpose |
| --- | --- | --- |
| Solidity compiler (`solc`) | `0.8.37` in the reported build | Compile Solidity contracts |
| Solidity Jupyter kernel | Custom implementation `1.0` | Compile Solidity directly in notebook cells |
| Ganache | `7.9.2` in the reported output | Local Ethereum-compatible blockchain |
| Hardhat | `2.26.3` | Smart contract development and testing |
| `@nomicfoundation/hardhat-ethers` | `3.0.8` | Hardhat integration with Ethers.js |
| Ethers.js | Major version `6`; exact patch not pinned | Ethereum JavaScript library |
| Foundry | Not explicitly pinned | Smart contract development toolkit |
| Forge | Installed through Foundry | Build, test, and deploy contracts |
| Cast | Installed through Foundry | Blockchain RPC and contract interaction |
| Anvil | Installed through Foundry | Local Ethereum development node |
| Chisel | Installed through Foundry | Interactive Solidity environment |

**Important:** The versions above reflect the Dockerfile configuration and the installation output previously reported. They are not a guarantee that every version has been verified in the final published image. In particular, Foundry is installed through `foundryup` without a pinned release, and the exact version can change between builds.

### Jupyter Kernel Inventory

The configured environment includes the following kernel families:

- Python — IPython / ipykernel
- C++ — jupyter-cpp-kernel
- Java — IJava
- Scala — Almond
- R — IRkernel
- Go — Gophernotes
- Rust — evcxr\_jupyter
- Julia — IJulia
- JavaScript — IJavascript
- Deno — Deno Jupyter
- Kotlin — Kotlin Jupyter Kernel
- Elixir — Custom Jupyter kernel
- Ruby — IRuby
- MATLAB-compatible computing — GNU Octave / octave\_kernel
- Bash — bash\_kernel
- C# and F# — .NET Interactive
- Solidity — Custom Solidity Jupyter kernel

Kernel availability should be confirmed using `jupyter kernelspec list` inside the built image.

## Version Verification

Run the following commands inside the container to inspect installed versions:

```
python --version
jupyter lab --version
java --version
scala -version
R --version
go version
rustc --version
julia --version
node --version
deno --version
dotnet --version
ruby --version
g++ --version
octave --version

solc --version
ganache --version

cd /opt/solidity-workspace
./node_modules/.bin/hardhat --version
npm ls --depth=0

forge --version
cast --version
anvil --version
chisel --version

jupyter kernelspec list
```

Some commands may be unavailable if an optional installation failed or a tool is not included in the final image.

## Build and Run

```
docker pull jorgecardona/datascience-mlops-kernels:latest

docker run -d \
  --name datascience-kernels \
  -p 8888:8888 \
  jorgecardona/datascience-mlops-kernels:latest
```

Open JupyterLab at `http://localhost:8888`.

## Reproducibility

To achieve fully reproducible builds, pin all relevant versions, including:

- Python packages and Jupyter extensions.
- APT package versions or a fixed base-image digest.
- npm dependencies and Foundry releases.
- Deno and .NET tool versions.
- Kernel package versions and language package environments.

The `latest` Docker tag is mutable and may point to different builds over time.

---

# Español

## Descripción general

Entorno Docker multilenguaje para Ciencia de Datos, Machine Learning, MLOps, computación científica, desarrollo de software e ingeniería blockchain.

Basada en Python 3.14, esta imagen integra varios lenguajes de programación, kernels de Jupyter, frameworks de desarrollo y herramientas blockchain en un entorno unificado de JupyterLab.

El objetivo es proporcionar un espacio de trabajo reproducible. Las versiones fijadas explícitamente en el Dockerfile se documentan a continuación. Los componentes instalados sin una versión explícita pueden cambiar entre compilaciones de la imagen.

## Lenguajes, herramientas y versiones

### Entorno base

| Componente | Versión | Instalación / Notas |
| --- | --- | --- |
| Python | `3.14.7` | Imagen base: `python:3.14.7` |
| JupyterLab | Última disponible durante la compilación | Instalado con `pip install --upgrade jupyterlab` |
| IPython Kernel | Última versión compatible durante la compilación | Instalado mediante `ipykernel` |
| CMake | Versión de la distribución | Instalado mediante APT |
| Compilador GNU C++ | Versión de la distribución | Instalado mediante `g++` y `build-essential` |

### Lenguajes de programación y runtimes

| Lenguaje / Runtime | Versión | Kernel / Implementación |
| --- | --- | --- |
| Python | `3.14.7` | IPython / ipykernel |
| Java | JDK `25` | IJava `1.3.0` |
| Scala | `2.13.18` | Almond `0.14.5` |
| R | Se solicita el paquete `4.5.0-3` | IRkernel; versión no fijada |
| Go | Versión de la distribución | Gophernotes `0.7.5` |
| Rust | Se solicita `1.98.1` | evcxr\_jupyter; versión no fijada |
| Julia | `1.13.0` | IJulia; versión del paquete no fijada |
| Node.js | `20.19.2` | IJavascript; versión no fijada |
| Deno | Última versión disponible del instalador | Deno Jupyter |
| Kotlin | Sin versión explícitamente fijada | Kotlin Jupyter Kernel |
| Elixir | Versión de la distribución | Kernel Jupyter personalizado |
| Ruby | Versión de la distribución | IRuby `0.8.3` |
| C++ | Compilador de la distribución | jupyter-cpp-kernel; versión no fijada |
| Entorno compatible con MATLAB | GNU Octave `9.4.0` solicitado | octave\_kernel `1.1.1` |
| Bash | Shell de la distribución | bash\_kernel; versión no fijada |
| C# | Canal del SDK .NET `10.0` | .NET Interactive; versión de la herramienta no fijada |
| F# | Canal del SDK .NET `10.0` | .NET Interactive; versión de la herramienta no fijada |
| Solidity | Paquete npm `solc` `0.8.37` en la compilación reportada | Kernel Jupyter personalizado `1.0` |
| JavaScript | Node.js `20.19.2` | IJavascript |
| TypeScript / JavaScript | Versión instalada por Deno | Deno Jupyter |

**Política de versiones:** Solicitar una versión no garantiza que esa versión haya quedado instalada. La disponibilidad de paquetes APT, los instaladores externos, la resolución de dependencias y las restricciones de compatibilidad pueden afectar al resultado final. La compilación Docker debe verificar las versiones realmente instaladas.

### Herramientas de desarrollo blockchain

| Herramienta | Versión / Configuración | Función |
| --- | --- | --- |
| Compilador Solidity (`solc`) | `0.8.37` en la salida reportada | Compilar contratos Solidity |
| Kernel Jupyter de Solidity | Implementación personalizada `1.0` | Compilar Solidity desde celdas del notebook |
| Ganache | `7.9.2` en la salida reportada | Blockchain local compatible con Ethereum |
| Hardhat | `2.26.3` | Desarrollo y pruebas de contratos inteligentes |
| `@nomicfoundation/hardhat-ethers` | `3.0.8` | Integración de Hardhat con Ethers.js |
| Ethers.js | Versión principal `6`; parche exacto no fijado | Biblioteca JavaScript para Ethereum |
| Foundry | Sin versión explícitamente fijada | Kit de herramientas para contratos inteligentes |
| Forge | Instalado mediante Foundry | Compilar, probar y desplegar contratos |
| Cast | Instalado mediante Foundry | Interacción con RPC y contratos |
| Anvil | Instalado mediante Foundry | Nodo local de desarrollo de Ethereum |
| Chisel | Instalado mediante Foundry | Entorno interactivo de Solidity |

**Importante:** Las versiones anteriores reflejan la configuración del Dockerfile y las salidas de instalación reportadas. No garantizan que todas hayan sido verificadas en la imagen publicada final. En particular, Foundry se instala mediante `foundryup` sin fijar una versión, por lo que puede cambiar entre compilaciones.

### Inventario de kernels de Jupyter

El entorno está configurado para incluir las siguientes familias de kernels:

- Python — IPython / ipykernel
- C++ — jupyter-cpp-kernel
- Java — IJava
- Scala — Almond
- R — IRkernel
- Go — Gophernotes
- Rust — evcxr\_jupyter
- Julia — IJulia
- JavaScript — IJavascript
- Deno — Deno Jupyter
- Kotlin — Kotlin Jupyter Kernel
- Elixir — Kernel Jupyter personalizado
- Ruby — IRuby
- Computación compatible con MATLAB — GNU Octave / octave\_kernel
- Bash — bash\_kernel
- C# y F# — .NET Interactive
- Solidity — Kernel Jupyter personalizado

Confirma la disponibilidad real de los kernels ejecutando `jupyter kernelspec list` dentro de la imagen construida.

## Verificación de versiones

Ejecuta estos comandos dentro del contenedor para consultar las versiones instaladas:

```
python --version
jupyter lab --version
java --version
scala -version
R --version
go version
rustc --version
julia --version
node --version
deno --version
dotnet --version
ruby --version
g++ --version
octave --version

solc --version
ganache --version

cd /opt/solidity-workspace
./node_modules/.bin/hardhat --version
npm ls --depth=0

forge --version
cast --version
anvil --version
chisel --version

jupyter kernelspec list
```

Algunos comandos pueden no estar disponibles si falla una instalación opcional o si una herramienta no está incluida en la imagen final.

## Construcción y ejecución

```
docker pull jorgecardona/datascience-mlops-kernels:latest

docker run -d \
  --name datascience-kernels \
  -p 8888:8888 \
  jorgecardona/datascience-mlops-kernels:latest
```

Abre JupyterLab en `http://localhost:8888`.

## Reproducibilidad

Para obtener compilaciones completamente reproducibles, fija todas las versiones relevantes, incluyendo:

- Paquetes Python y extensiones de Jupyter.
- Versiones de paquetes APT o un digest fijo de la imagen base.
- Dependencias npm y versiones de Foundry.
- Versiones de Deno y de las herramientas .NET.
- Versiones de los paquetes de kernels y de los entornos de cada lenguaje.

La etiqueta Docker `latest` es mutable y puede apuntar a diferentes compilaciones con el paso del tiempo.

---

## Repositorio y distribución

- **GitHub:** https://github.com/JorgeCardona/dockerhub-datascience-mlops-kernels
- **Docker Hub:** [https://hub.docker.com/r/jorgecardona/datascience-mlops-kernels](<https://hub.docker.com/r/jorgecardona/datascience-mlops-kernels>)

### Una precisión importante sobre tu Dockerfile

Hay varias versiones que conviene corregir o verificar antes de afirmar que la imagen está completamente fijada:

- R: `R_VERSION=4.5.0-3` corresponde a la versión del paquete Debian solicitada, no necesariamente a la versión upstream de R que muestra `R --version`.
- Rust: `1.98.1` debe comprobarse en el canal de distribución configurado; si esa versión no está disponible, la compilación fallará.
- Foundry: `foundryup` sin una versión concreta no produce una instalación reproducible.
- Ganache: `npm install -g ganache` sin versión instala la versión que npm resuelva en ese momento.
- JupyterLab, Kotlin, C++, Deno y otros paquetes: varias instalaciones utilizan versiones sin fijar.
- Solidity: el kernel personalizado indica `language_version = "0.8.37"`, pero conviene validar ese dato contra `solc --version` durante la compilación.

Para que el README refleje las versiones reales de cada publicación, lo ideal es generar automáticamente una tabla de versiones durante el build y conservarla como artefacto de la imagen.