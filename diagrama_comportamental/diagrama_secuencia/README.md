## **PLANILLA ESCOLAR**


## DESCRIPCION DEL PROBLEMA

- El problema a resolver se centra en la necesidad de un sistema académico que facilite la interacción y gestión de la información entre estudiantes, profesores y administradores. Este sistema debe permitir el registro y autenticación de usuarios, garantizando que cada uno acceda a las funciones pertinentes según su rol, como estudiantes, profesores o administradores. Los estudiantes requieren acceso a sus propias notas para monitorear su rendimiento académico, mientras que los profesores necesitan herramientas para registrar y modificar las calificaciones de sus estudiantes de manera eficiente. Además, es fundamental que los profesores puedan registrar la asistencia diaria, permitiendo un seguimiento preciso de la presencia en clase. El administrador del sistema debe tener un control total sobre los datos académicos y de usuarios, lo que incluye la gestión de notas, asistencia y cursos, asegurando que se mantenga la integridad de la información. Asimismo, se requiere un sistema que registre las notas y asistencia, implemente reglas de negocio como el cálculo de promedios y notificaciones automáticas cuando un estudiante falte más de un número específico de veces. Es esencial que el sistema cumpla con restricciones de seguridad y funcionalidad, como la unicidad de los nombres de usuario y la validación de contraseñas, para proteger la información y asegurar que solo los usuarios autorizados puedan realizar acciones específicas. En conjunto, este problema abarca la creación de un sistema integral que permita un manejo organizado y seguro de la información académica, atendiendo las necesidades de todos los usuarios involucrados.

## Diagrama de casos de uso
![](/out/diagrama_comportamental/diagrama_secuencia/diagrama/diagrama.png)

## codigo PlantUML:

```sql

@startuml
actor Profesor
actor Estudiante
boundary Sistema as Sistema
database BD as BaseDeDatos

Profesor -> Sistema : Iniciar sesión
Sistema -> BaseDeDatos : Validar credenciales(Profesor)
BaseDeDatos --> Sistema : Credenciales válidas
Sistema --> Profesor : Acceso concedido

Estudiante -> Sistema : Iniciar sesión
Sistema -> BaseDeDatos : Validar credenciales(Estudiante)
BaseDeDatos --> Sistema : Credenciales válidas
Sistema --> Estudiante : Acceso concedido

group Profesor gestiona curso y asigna nota
    Profesor -> Sistema : Ver cursos asignados
    Sistema -> BaseDeDatos : Obtener cursos(Profesor)
    BaseDeDatos --> Sistema : Lista de cursos
    Sistema --> Profesor : Mostrar lista de cursos

    Profesor -> Sistema : Asignar nota a estudiante
    Sistema -> BaseDeDatos : Guardar nota(Estudiante, Materia)
    BaseDeDatos --> Sistema : Confirmar guardado de nota
    Sistema --> Profesor : Nota asignada con éxito
end

group Estudiante consulta sus notas y asistencia
    Estudiante -> Sistema : Ver notas
    Sistema -> BaseDeDatos : Obtener notas(Estudiante)
    BaseDeDatos --> Sistema : Devolver notas
    Sistema --> Estudiante : Mostrar notas

    Estudiante -> Sistema : Ver asistencia
    Sistema -> BaseDeDatos : Obtener asistencia(Estudiante)
    BaseDeDatos --> Sistema : Devolver registros de asistencia
    Sistema --> Estudiante : Mostrar asistencia
end

@enduml
