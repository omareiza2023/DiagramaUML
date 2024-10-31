# **PLANILLA ESCOLAR**


## DESCRIPCION DEL PROBLEMA

- El problema a resolver se centra en la necesidad de un sistema académico que facilite la interacción y gestión de la información entre estudiantes, profesores y administradores. Este sistema debe permitir el registro y autenticación de usuarios, garantizando que cada uno acceda a las funciones pertinentes según su rol, como estudiantes, profesores o administradores. Los estudiantes requieren acceso a sus propias notas para monitorear su rendimiento académico, mientras que los profesores necesitan herramientas para registrar y modificar las calificaciones de sus estudiantes de manera eficiente. Además, es fundamental que los profesores puedan registrar la asistencia diaria, permitiendo un seguimiento preciso de la presencia en clase. El administrador del sistema debe tener un control total sobre los datos académicos y de usuarios, lo que incluye la gestión de notas, asistencia y cursos, asegurando que se mantenga la integridad de la información. Asimismo, se requiere un sistema que registre las notas y asistencia, implemente reglas de negocio como el cálculo de promedios y notificaciones automáticas cuando un estudiante falte más de un número específico de veces. Es esencial que el sistema cumpla con restricciones de seguridad y funcionalidad, como la unicidad de los nombres de usuario y la validación de contraseñas, para proteger la información y asegurar que solo los usuarios autorizados puedan realizar acciones específicas. En conjunto, este problema abarca la creación de un sistema integral que permita un manejo organizado y seguro de la información académica, atendiendo las necesidades de todos los usuarios involucrados.

## Diagrama de casos de uso
![](/diagrama_comportamental/diagrama_colaboracion/img/a.png)

## codigo PlantUML:

```sql

@startuml a
!define DATABASE database
allowmixing

class Persona
class Usuario
class Autenticacion
class UsuarioAutenticado
class Nota
class Asistencia
class Curso
class Estudiante
class Profesor
class Administrador
class Planilla

DATABASE DBUser
DATABASE DBAdmin

Persona <|-- Usuario
Usuario --> Autenticacion
Autenticacion --> DBUser

UsuarioAutenticado --> Profesor
UsuarioAutenticado --> Estudiante
UsuarioAutenticado --> Administrador

' Relaciones de acceso
DBAdmin --> Asistencia : acceso total
DBAdmin --> Curso : acceso total
DBAdmin --> Nota : acceso total
DBAdmin --> Planilla : acceso total

' Flechas de acceso
DBAdmin --|> Administrador : acceso global
Asistencia <--o Profesor : acceso limitado
Nota <--o Profesor : acceso limitado
Planilla <--o Estudiante : acceso limitado

@enduml
´´´
