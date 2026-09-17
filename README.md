# dockerhub-datascience-mlops-kernels

![JupyterLab Kernels](https://raw.githubusercontent.com/JorgeCardona/dockerhub-datascience-mlops-kernels/refs/heads/main/images/kernels.png)

Entorno Docker de alto rendimiento optimizado para Ciencia de Datos y MLOps, con soporte nativo para **15 kernels e intérpretes multi-lenguaje** preconfigurados en JupyterLab sobre una base Python 3.14.

---

## 🚀 Lenguajes e Intérpretes Soportados

* **Python 3.14** (Data Science & MLOps Stack)
* **C++20** (`jupyter-cpp-kernel`)
* **Java 25** (`IJava` kernel)
* **Scala** (`Almond` kernel)
* **R 4.5** (`IRkernel`)
* **Julia** (`IJulia`)
* **Kotlin** (`kotlin-jupyter`)
* **Elixir** (`IElixir`)
* **MATLAB / Octave** (`octave_kernel`)
* **Node.js / JavaScript** (`ijavascript`)
* **Deno** (`deno jupyter`)
* **Go** (`gophernotes`)
* **Rust** (`evcxr_jupyter`)
* **Ruby** (`IRuby`)
* **Bash** (`bash_kernel`)

---

## 📦 Características Principales

* **Capa Única Optimizada:** Limpieza del gestor de paquetes (`/var/lib/apt/lists/*`) integrada en cada capa `RUN` para minimizar el tamaño final de la imagen.
* **Integración con Git:** Incluye la extensión `jupyterlab-git` preinstalada y habilitada.
* **Espacio de Trabajo Listo:** Directorio persistente `/notebooks` listo para vincular volúmenes locales.

---

## 🛠️ Uso Rápido

```bash
docker run -d \
  -p 8888:8888 \
  -v $(pwd)/notebooks:/notebooks \
  --name datascience-kernels \
  jorgecardona/datascience-mlops-kernels:latest
