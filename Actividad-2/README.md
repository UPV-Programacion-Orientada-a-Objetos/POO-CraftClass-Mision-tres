# Implementación Paralela de Merge Sort y Quick Sort en Java

**Descripción:**

Se deberá implementar los algoritmos de ordenamiento Merge Sort y Quick Sort utilizando concurrencia/paralelismo en el lenguaje de programación Java. Ambos algoritmos deben ser capaces de ordenar una lista de elementos de manera eficiente y paralela utilizando hilos (threads).

**Requisitos del Sistema:**

1. **Merge Sort Paralelo:** Implementar el algoritmo de ordenamiento Merge Sort de manera que divida la lista en sub-listas más pequeñas y ordene estas sub-listas en paralelo utilizando hilos. Luego, fusionar las sub-listas ordenadas en el orden correcto.

2. **Quick Sort Paralelo:** Implementar el algoritmo de ordenamiento Quick Sort de manera que divida la lista en particiones y ordene las particiones en paralelo utilizando hilos. Luego, combinar las particiones ordenadas en el orden correcto.

3. **Concurrencia/Paralelismo:** Utilizar el paquete `java.util.concurrent` de Java para gestionar la concurrencia y la creación de hilos.

**Algoritmo de Merge Sort:**

```markdown

Function MergeSort(arr, left, right)
  If left < right
    mid ← (left + right) / 2
    MergeSort(arr, left, mid)
    MergeSort(arr, mid + 1, right)
    Merge(arr, left, mid, right)
  End If
End Function
```

Este código Markdown representa la misma función `MergeSort` en un formato más legible para la plataforma.

**Algoritmo de Quick Sort:**

```markdown
Function QuickSort(arr, low, high)
  If low < high
    pivotIndex ← Partition(arr, low, high)
    QuickSort(arr, low, pivotIndex - 1)
    QuickSort(arr, pivotIndex + 1, high)
  End If
End Function
```

Este código Markdown representa la misma función `QuickSort` en un formato más legible para la plataforma.

**Entregables:**

Los estudiantes deben entregar los siguientes elementos:

1. **Código Fuente:** El código fuente completo de las implementaciones paralelas de Merge Sort y Quick Sort en Java.

2. **Pruebas Unitarias:** Deben proporcionar pruebas unitarias que demuestren que los algoritmos de ordenamiento funcionan correctamente en un entorno paralelo. Las pruebas deben incluir casos con listas desordenadas de diferentes tamaños.

3. **Informe:** Un informe breve que explique el enfoque utilizado para implementar la concurrencia/paralelismo en los algoritmos, las observaciones sobre el rendimiento y cualquier problema o desafío encontrado durante la implementación.

**Fecha de Entrega:**

La fecha de entrega de esta tarea se especificará en el calendario académico o por el profesor. Asegúrate de cumplir con la fecha límite establecida.

**Evaluación:**

Los proyectos serán evaluados en función de los siguientes criterios:

1. **Funcionalidad:** Los algoritmos de ordenamiento Merge Sort y Quick Sort deben funcionar correctamente y producir resultados ordenados.

2. **Concurrencia/Paralelismo:** La implementación de la concurrencia/paralelismo debe ser eficiente y efectiva.

3. **Pruebas Unitarias:** Las pruebas unitarias deben cubrir una variedad de casos y demostrar que los algoritmos funcionan de manera robusta y sin errores en un entorno paralelo.

4. **Informe:** El informe deberá contener un estudio estadístico de el tiempo y recursos utilizados cuando se tienen: 100, 100K, 1M, 5M, 10M de datos a ordenar.

Esta tarea brinda a los estudiantes la oportunidad de aplicar sus conocimientos en concurrencia y paralelismo en un contexto práctico al implementar algoritmos de ordenamiento eficientes.

---

## Ejemplos.

Se puede utilizar el siguiente bloque de código para generar 10,000,000 de registros de una base de datos ficticia; con la intención de evaluar el rendimiento de los algoritmos solicitados.

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

public class GeneradorRegistros {
    public static void main(String[] args) {
        int totalRegistros = 10000000;
        List<Registro> registros = new ArrayList<>();

        for (int i = 0; i < totalRegistros; i++) {
            Registro registro = generarRegistroAleatorio();
            registros.add(registro);
        }

        // Ahora tienes 10,000,000 de registros ficticios en la lista "registros"
        // Puedes realizar operaciones de inserción en tu base de datos a partir de aquí
    }

    // Clase para representar un registro ficticio
    static class Registro {
        String nombre;
        String apellido;
        int edad;
        String direccion;
        // Puedes agregar más campos según tus necesidades

        Registro(String nombre, String apellido, int edad, String direccion) {
            this.nombre = nombre;
            this.apellido = apellido;
            this.edad = edad;
            this.direccion = direccion;
        }
    }

    // Método para generar un registro ficticio aleatorio
    static Registro generarRegistroAleatorio() {
        String[] nombres = {"Alice", "Bob", "Charlie", "David", "Eva", "Frank", "Grace", "Helen", "Ivan", "Jack"};
        String[] apellidos = {"Smith", "Johnson", "Brown", "Lee", "Chen", "Garcia", "Kim", "Lopez", "Patel", "Taylor"};
        String[] direcciones = {"Calle A", "Avenida B", "Calle C", "Avenida D", "Calle E"};

        Random random = new Random();
        String nombre = nombres[random.nextInt(nombres.length)];
        String apellido = apellidos[random.nextInt(apellidos.length)];
        int edad = random.nextInt(80) + 18; // Edad entre 18 y 97
        String direccion = direcciones[random.nextInt(direcciones.length)];

        return new Registro(nombre, apellido, edad, direccion);
    }
}
```

Este código generará una lista de 10,000,000 de registros ficticios en la lista `registros`. Puedes adaptar la estructura de la clase `Registro` y los datos generados en `generarRegistroAleatorio()` según los campos.