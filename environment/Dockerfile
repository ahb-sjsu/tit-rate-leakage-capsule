FROM registry.codeocean.com/codeocean/py-r:python3.12.8-R4.4.2-JupyterLab4.3.5-RStudiorstudio-server-2024.12.1-563-ubuntu22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN pip install -U --no-cache-dir \
    numpy==2.2.6 \
    scipy==1.17.1 \
    cvxpy==1.9.2 \
    sympy==1.14.0
