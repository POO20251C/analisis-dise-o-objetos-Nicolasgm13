[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vTkcPn0-)
# 2.-Dise-o-Orientado-a-Objetos
Primer acercamiento y prácticas guiadas e individuales de POO

# Diagrama UML - Caso Biblioteca

```mermaid
classDiagram
    %% ========== CLASES ==========
    
    class Biblioteca {
        - String nombre
        - List~Libro~ catalogo
        - List~Lector~ lectores
        - List~Prestamo~ prestamos
        + agregarLibro(libro: Libro): void
        + registrarLector(lector: Lector): void
        + realizarPrestamo(libro: Libro, lector: Lector): Prestamo
        + devolverLibro(prestamo: Prestamo): void
        + buscarLibroPorISBN(isbn: String): Libro
        + listarLibrosDisponibles(): List~Libro~
    }

    class Libro {
        - String titulo
        - String ISBN
        - int anyoPublicacion
        - boolean disponible
        + marcarComoPrestado(): void
        + marcarComoDisponible(): void
        + obtenerInformacion(): String
    }

    class Lector {
        - String nombre
        - int numeroSocio
        - Date fechaRegistro
        - List~Prestamo~ historialPrestamos
        + solicitarPrestamo(libro: Libro): Prestamo
        + devolverLibro(prestamo: Prestamo): void
        + obtenerHistorial(): List~Prestamo~
    }

    class Prestamo {
        - Libro libro
        - Lector lector
        - Date fechaPrestamo
        - Date fechaDevolucion
        - boolean estado
        + registrarDevolucion(): void
        + obtenerDetalles(): String
    }

    class Clases{
        - Biblioteca
        - Libro
        - Lector
        - Prestamo   
    }
     class Relaciones {
        - Biblioteca → Libros (`1 -- 0..*`) 
        - Biblioteca → Lectores (`1 -- 0..*`)
        - Biblioteca → Préstamos (`1 -- 0..*`)
        - Lector → Préstamos (`1 -- 0..*`) 
        - Préstamo → Libro (`1 -- 1`)
        - Libro → Préstamo (`1 -- 0..1`)
    }
    
	
    %% ========== RELACIONES Y CARDINALIDAD ==========
    
    Biblioteca "1" -- "0..*" Libro : 
    Biblioteca "1" -- "0..*" Lector : 
    Biblioteca "1" -- "0..*" Prestamo : 
    
    Lector "1" -- "0..*" Prestamo : 
    Prestamo "1" -- "1" Libro : 
    
    Libro "1" -- "0..1" Prestamo : 

