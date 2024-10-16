# sqlserver-docker
Base sqlserver-windows on docker for local test.





## **Guia para restaurar certificados - (Docker)**

**Código de ejemplo de sqlserver base para windows/linux:** **
**https://github.com/Ablfantastic/sqlserver-docker

1. **compose.yaml**

*login en azure:* az acr login -n acrsabentisimages

*imagen* : acrsabentisimages.azurecr.io/windowscontainers/sqlserver2022base:v1.0.6

![img](https://lh7-rt.googleusercontent.com/docsz/AD_4nXenCLAcGIAulf8wi9TF9mJ3F22UHzjSII6mhD4RxGJaNmpkJQB5qWsVhWOye0JD1OrnO37gNPveWw_UAlq7HBgfhQZGw3Gc1k3ZY3PdmfCELabK_1Ain9PT1zu697ytu7NzYrSHaPIQE7qOzBdKSsVzOP51?key=PU9bhJ3U7ZXMHu3rK2yQEg)

Al montar un volumen en el directorio D:/ es necesario poner los archivos necesarios para restaurar la bd (.zip con certificados, .bak, script para restaurar certificados) en una carpeta con el nombre del volumen definido en el compose.yaml en el host.
**ej: D:/sqlserver2022test**

![image-20241016131642683](C:\Users\AbelGallardo\AppData\Roaming\Typora\typora-user-images\image-20241016131642683.png)



2. **Comprovar la conexión al sqlserver:**

![img](https://lh7-rt.googleusercontent.com/docsz/AD_4nXf1ySI-Kg_ddMwaVEDv3kv2mCrfqh4bRwc6Rcdgor6Dy95mKM00yl65XLL6tkg4aDrcSy2sXYzMoQ5txx3VsmcoXZmKzCTsUSgsEk_Ye8Tm8JBOVCJhOZ2LX6-8FWFbWXHh7s1XcBdLKZ093tgRQT-K2ds?key=PU9bhJ3U7ZXMHu3rK2yQEg)

3. **Entrar al contenedor y restaurar los certificados**

![img](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe3PSJMu9HHyxNi48Q_skj1OLaKdKQP2rGKsqbYjILs2_5kO1zEgT9Gde34T4u6hm1ktX7VbKE2dcl1nq9Rv18A0kwqSb_TZoSTxFimMvwA3TxPMmREDBMld3Izgb65Igql0cC5pjjgTxNcOM5CG1hECy3U?key=PU9bhJ3U7ZXMHu3rK2yQEg)

Ir al volumen creado (D:/) y ejecutar el script `restoreCertificateFromZip.ps1`

**es posible que falten permisos, en ese caso: 
	`Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`

`sqlinstance: 192.168.1.5 (server name)`

`zipPath: certificados.zip` 

4. **Restaurar la BD desde sqlserver.** 
