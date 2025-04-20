# 🐳 Arquitectura Docker Compose
Este proyecto levanta un entorno completo para ML usando Docker Compose:

```

+-------------------+         +-----------------+         +---------------------+
|                   |         |                 |         |                     |
|   JupyterLab      +-------->+     MLflow      +-------->+     PostgreSQL      |
|  (cnt_jupyterlab) |  HTTP   | (cnt_mlflow)    |  SQL    |  (cnt_postgresql)   |
|                   |         |                 |         |                     |
+--------+----------+         +--------+--------+         +-----------+---------+
         |                             |                                |
         |   Volumen local:            |   Volumen local:              |
         |   ../mis-archivos/proyectos |   ../mis-archivos/mlruns      |
         |                             |                                |
         v                             v                                v
/home/jovyan/work          /home/jovyan/work                  /var/lib/postgresql/data

                 Todos los contenedores están en la red virtual: ml_net
```
