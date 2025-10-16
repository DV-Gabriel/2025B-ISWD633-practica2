# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

Mis conocimientos anteriores respecto a docker eran casi nulos, sabia algunos comandos debido a que son similares a linux, pero despues de la práctica aprendí más comandos y el papel clave de las variables de entorno, las redes y los volúmenes para el funcionamiento de las aplicaciones. 
Por otro lado un problema clave fue resolver el problema de WordPress usando docker logs lo que me permitió identificar que faltaba crear la base de datos, aunque posteriormente se creaba la base de datos en Mysql.

Consultar: Cómo se gestionan datos confidenciales con los secretos de Docker (Docker Secrets).
Docker Secrets es una funcionalidad diseñada para almacenar y gestionar de forma segura información confidencial que las aplicaciones necesitan para funcionar, como contraseñas, claves API, certificados o tokens. En lugar de guardar estos datos directamente en variables de entorno o archivos dentro de la imagen (lo cual es inseguro), Docker Secrets los mantiene encriptados y accesibles solo para los contenedores autorizados.

Cuando se utiliza Docker Swarm, los secretos se almacenan en el managers del clúster de manera cifrada y se distribuyen únicamente a los nodos que ejecutan servicios que los necesitan. Una vez entregados, los secretos se montan dentro del contenedor como archivos de solo lectura (generalmente en /run/secrets/), evitando que queden expuestos en imágenes, variables o registros.

Aqui algunos comandos usados:
Crear un secreto 
'''
echo "mi_clave_secreta" | docker secret create api_key -
'''

Ver secretos disponobles 
'''
docker secret ls
'''

Usar el secreto en un servicio
'''
docker service create --name app --secret api_key nginx

'''
