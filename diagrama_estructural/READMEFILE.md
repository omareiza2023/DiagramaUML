## **PLANILLA ESCOLAR**


## DESCRIPCION DEL PROBLEMA

- El problema a resolver se centra en la necesidad de un sistema académico que facilite la interacción y gestión de la información entre estudiantes, profesores y administradores. Este sistema debe permitir el registro y autenticación de usuarios, garantizando que cada uno acceda a las funciones pertinentes según su rol, como estudiantes, profesores o administradores. Los estudiantes requieren acceso a sus propias notas para monitorear su rendimiento académico, mientras que los profesores necesitan herramientas para registrar y modificar las calificaciones de sus estudiantes de manera eficiente. Además, es fundamental que los profesores puedan registrar la asistencia diaria, permitiendo un seguimiento preciso de la presencia en clase. El administrador del sistema debe tener un control total sobre los datos académicos y de usuarios, lo que incluye la gestión de notas, asistencia y cursos, asegurando que se mantenga la integridad de la información. Asimismo, se requiere un sistema que registre las notas y asistencia, implemente reglas de negocio como el cálculo de promedios y notificaciones automáticas cuando un estudiante falte más de un número específico de veces. Es esencial que el sistema cumpla con restricciones de seguridad y funcionalidad, como la unicidad de los nombres de usuario y la validación de contraseñas, para proteger la información y asegurar que solo los usuarios autorizados puedan realizar acciones específicas. En conjunto, este problema abarca la creación de un sistema integral que permita un manejo organizado y seguro de la información académica, atendiendo las necesidades de todos los usuarios involucrados.

## Diagrama de casos de uso
![](/diagrama_estructural/out/diagrama_estructural/)

## codigo PlantUML:

```sql

@startuml

class Usuario {
    +usuario_id: INT
    +nombre_usuario: VARCHAR(50)
    +contraseña: VARCHAR(255)
}

class Persona {
    +persona_id: INT
    +nombre: VARCHAR(100)
    +correo: VARCHAR(100)
    +rol: ENUM
    +usuario_id: INT
}

class Curso {
    +curso_id: INT
    +nombre_curso: VARCHAR(100)
    +aula: VARCHAR(50)
}

class Persona_Curso {
    +persona_id: INT
    +curso_id: INT
    +rol_curso: ENUM
}

class Materia {
    +materia_id: INT
    +nombre_materia: VARCHAR(100)
    +curso_id: INT
}

class Nota {
    +nota_id: INT
    +estudiante_id: INT
    +materia_id: INT
    +nota: DECIMAL(3, 2)
    +fecha_evaluacion: DATE
}

class Nota_Final {
    +nota_final_id: INT
    +estudiante_id: INT
    +curso_id: INT
    +nota_final: DECIMAL(3, 2)
    +estado_aprobacion: ENUM
}

class Asistencia {
    +asistencia_id: INT
    +estudiante_id: INT
    +curso_id: INT
    +fecha: DATE
    +presente: BOOLEAN
}

Persona "1" -- "0..1" Usuario : "tiene"
Persona_Curso "0..*" -- "1" Persona : "inscribe"
Persona_Curso "0..*" -- "1" Curso : "contiene"
Materia "0..*" -- "1" Curso : "pertenece"
Nota "0..*" -- "1" Persona : "evaluado"
Nota "0..*" -- "1" Mater


