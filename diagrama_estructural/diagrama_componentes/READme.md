# **PLANILLA ESCOLAR**


## DESCRIPCION DEL PROBLEMA

- El problema a resolver se centra en la necesidad de un sistema académico que facilite la interacción y gestión de la información entre estudiantes, profesores y administradores. Este sistema debe permitir el registro y autenticación de usuarios, garantizando que cada uno acceda a las funciones pertinentes según su rol, como estudiantes, profesores o administradores. Los estudiantes requieren acceso a sus propias notas para monitorear su rendimiento académico, mientras que los profesores necesitan herramientas para registrar y modificar las calificaciones de sus estudiantes de manera eficiente. Además, es fundamental que los profesores puedan registrar la asistencia diaria, permitiendo un seguimiento preciso de la presencia en clase. El administrador del sistema debe tener un control total sobre los datos académicos y de usuarios, lo que incluye la gestión de notas, asistencia y cursos, asegurando que se mantenga la integridad de la información. Asimismo, se requiere un sistema que registre las notas y asistencia, implemente reglas de negocio como el cálculo de promedios y notificaciones automáticas cuando un estudiante falte más de un número específico de veces. Es esencial que el sistema cumpla con restricciones de seguridad y funcionalidad, como la unicidad de los nombres de usuario y la validación de contraseñas, para proteger la información y asegurar que solo los usuarios autorizados puedan realizar acciones específicas. En conjunto, este problema abarca la creación de un sistema integral que permita un manejo organizado y seguro de la información académica, atendiendo las necesidades de todos los usuarios involucrados.

## Diagrama de casos de uso
![Diagrama de componentes](/diagrama_estructural/diagrama_componentes/img/componentes.png)

## codigo PlantUML:

```sql
@startuml
package "Sistema de Planilla Académica" {
    [Aplicación Web] as AplicacionWeb

    component "Autenticación" as Auth
    component "Gestión de Usuarios" as GestionUsuarios
    component "Gestión de Cursos" as GestionCursos
    component "Gestión de Materias" as GestionMaterias
    component "Gestión de Notas" as GestionNotas
    component "Gestión de Asistencia" as GestionAsistencia

    database "Base de Datos" as BD
}

AplicacionWeb --> Auth : Iniciar sesión
Auth --> BD : Validar credenciales

Auth --> GestionUsuarios : Autenticar usuario
AplicacionWeb --> GestionUsuarios : Registrar usuario

GestionUsuarios --> BD : Guardar información de usuario

AplicacionWeb --> GestionCursos : Acceder a cursos
GestionCursos --> BD : Obtener y guardar cursos
GestionCursos --> GestionMaterias : Relacionar materias con cursos

AplicacionWeb --> GestionMaterias : Acceder a materias
GestionMaterias --> BD : Obtener y guardar materias

AplicacionWeb --> GestionNotas : Acceder a notas
GestionNotas --> BD : Guardar y obtener notas

AplicacionWeb --> GestionAsistencia : Acceder a asistencia
GestionAsistencia --> BD : Guardar y obtener registros de asis
´´´