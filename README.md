# Workflow-CI
Repository ini menggunakan **MLflow Project** dan **GitHub Actions**. Workflow ini melakukan *re-training model secara otomatis*, menyimpan artefak model, serta membangun dan mempublikasikan **Docker Image** ke Docker Hub

## Teknologi yang Digunakan

* **Python 3.9**
* **MLflow**
* **scikit-learn**
* **pandas**
* **GitHub Actions**
* **Docker & Docker Hub**

## Alur Workflow CI

1. **Trigger Workflow**

   * Workflow berjalan otomatis ketika terjadi `push` ke branch `main`.

2. **Training Model dengan MLflow Project**

   * GitHub Actions menjalankan `mlflow run`.
   * Model dilatih ulang menggunakan dataset hasil preprocessing.
   * Parameter, metrik, dan model disimpan sebagai artefak MLflow.

3. **Penyimpanan Artefak**

   * Folder `mlruns` dihasilkan saat runtime.
   * Artefak diunggah sebagai **GitHub Actions Artifacts** 

4. **Build Docker Image (Advance)**

   * Docker image dibangun menggunakan perintah:

     ```bash
     mlflow models build-docker
     ```

5. **Push ke Docker Hub (Advance)**

   * Docker image dipublikasikan ke Docker Hub secara otomatis melalui CI.


## Artefak MLflow

Artefak MLflow (`mlruns`) dapat diunduh melalui:
GitHub Repository → Actions → Workflow Run → Artifacts


## Docker Hub

Docker image hasil training tersedia pada tautan berikut: https://hub.docker.com/r/nadiraasf/mlflow-ci
Link ini juga disertakan pada file: MLProject/dockerhub.txt

