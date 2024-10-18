# Proyecto_AWS_cluster_EKS

En este proyecto, vamos a desplegar, la aplicación web, en un clúster de Kubernetes.

## Escenario:
Tenemos un "Multitier Web Application Stack", que ya debería de estar contenedorizada y vamos a utilizar a nuestro proyecto "delta" y también tiene que estar "testeada".
Y ahora, vamos a Hostearla para producción. Ejecutar los contenedores para producción es diferente:

## Requisitos PARA ESTE nuevo proyecto:

- Alta Disponibilidad. (Para que nuestros contenedores no se caigan) (Y también necesitamos la Alta Disponibilidad, para el "nodo de cómputo".
- Tolerancia a fallos, si algo pasa a los contenedores y no responden, tambiñen deberían ser capaces de "auto-curarse".
- Debería de ser fácil de escalar los contenedores y los recursos de cómputo en donde nuestro contenedores están corriendo.
- Platform Independent, y también portable, flexible y ágil. Básicamente, deberíamos de ser capaces, de correr nuestros contenedores de forma local, en máquinas virtuales y debería de correr en "dev QA production".


Vamos a utilizar el orquestador de contenedores, Kubernetes, que es el mejor orquestador de contenedores.

Y vamos a utilizar el Java Stack, el proyecto "delta".

## Pasos:
- Necesitamos un clúster de Kubernetes, voy a utilizar "kOps", para iniciar mi Clúster de Kubernetes.
- Tener contenedorizada nuestra app, "delta". Sabemos, que en "delta", tenemos un contenedor MySQL que necesita volumen para almacenar los datos, y así tenga datos PERSISTENTES, QUE NO SE BORREN.
- Por lo tanto, vamos a crear un volumen EBS, para nuestro Pod de la BD.
- Vamos a etiquetar los nodos, con nombres de zonas.
- Vamos a crear, volumenes EBS en una zona y necesitamos nuestro pod, que esté corriendo en el mismo Nodo o en la misma Zona, donde creamos el volumen EBS.
- **Una vez tengamos todo esto**, vamos a crear el Kubernetes Definition File para crear nuestros objetos en el clúster de Kubernetes.
- Vamos a utilizar, "deployment, service, secret y volume".
