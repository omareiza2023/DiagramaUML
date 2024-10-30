## Diagrama de objetos

## **PLANILLA ESCOLAR**


## DESCRIPCION DEL PROBLEMA

- El problema a resolver se centra en la necesidad de un sistema académico que facilite la interacción y gestión de la información entre estudiantes, profesores y administradores. Este sistema debe permitir el registro y autenticación de usuarios, garantizando que cada uno acceda a las funciones pertinentes según su rol, como estudiantes, profesores o administradores. Los estudiantes requieren acceso a sus propias notas para monitorear su rendimiento académico, mientras que los profesores necesitan herramientas para registrar y modificar las calificaciones de sus estudiantes de manera eficiente. Además, es fundamental que los profesores puedan registrar la asistencia diaria, permitiendo un seguimiento preciso de la presencia en clase. El administrador del sistema debe tener un control total sobre los datos académicos y de usuarios, lo que incluye la gestión de notas, asistencia y cursos, asegurando que se mantenga la integridad de la información. Asimismo, se requiere un sistema que registre las notas y asistencia, implemente reglas de negocio como el cálculo de promedios y notificaciones automáticas cuando un estudiante falte más de un número específico de veces. Es esencial que el sistema cumpla con restricciones de seguridad y funcionalidad, como la unicidad de los nombres de usuario y la validación de contraseñas, para proteger la información y asegurar que solo los usuarios autorizados puedan realizar acciones específicas. En conjunto, este problema abarca la creación de un sistema integral que permita un manejo organizado y seguro de la información académica, atendiendo las necesidades de todos los usuarios involucrados.

## Diagrama de casos de uso
![](/out/diagrama_estructural/diagrama_objetos/objeto/objeto.png)

## codigo PlantUML:

```sql

@startuml

object usuario1 {
    usuario_id = 1
    nombre_usuario = "profesor01"
    contraseña = "abc123"
}

object usuario2 {
    usuario_id = 2
    nombre_usuario = "estudiante01"
    contraseña = "def456"
}

object persona1 {
    persona_id = 1
    nombre = "Juan Pérez"
    correo = "juan.perez@ejemplo.com"
    rol = "Profesor"
    usuario_id = 1
}

object persona2 {
    persona_id = 2
    nombre = "Ana Gómez"
    correo = "ana.gomez@ejemplo.com"
    rol = "Estudiante"
    usuario_id = 2
}

object curso1 {
    curso_id = 1
    nombre_curso = "Matemáticas"
    aula = "101"
}

object persona_curso1 {
    persona_id = 1
    curso_id = 1
    rol_curso = "Profesor"
}

object persona_curso2 {
    persona_id = 2
    curso_id = 1
    rol_curso = "Estudiante"
}

object materia1 {
    materia_id = 1
    nombre_materia = "Álgebra"
    curso_id = 1
}

object nota1 {
    nota_id = 1
    estudiante_id = 2
    materia_id = 1
    nota = 9.5
    fecha_evaluacion = "2024-10-29"
}

object nota_final1 {
    nota_final_id = 1
    estudiante_id = 2
    curso_id = 1
    nota_final = 9.0
    estado_aprobacion = "Aprobado"
}

object asistencia1 {
    asistencia_id = 1
    estudiante_id = 2
    curso_id = 1
    fecha = "2024-10-28"
    presente = true
}

persona1 -- usuario1 : "es usuario de"
persona2 -- usuario2 : "es usuario de"
persona1 -- persona_curso1 : "inscrito en curso"
persona2 -- persona_curso2 : "inscrito en curso"
curso1 -- persona_curso1 : "contiene"
curso1 -- persona_curso2 : "contiene"
materia1 -- curso1 : "pertenece"
nota1 -- persona2 : "tiene nota"
nota1 -- materia1 : "evaluado en"
nota_final1 -- persona2 : "tiene nota final"
nota_final1 -- curso1 : "para curso"
asistencia1 -- persona2 : "asistencia registrada"
asistencia1 -- curso1 : "pertenece"

@enduml

