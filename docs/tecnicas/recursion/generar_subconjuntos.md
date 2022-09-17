# Generar subconjuntos

Veamos cómo generar todos los subconjuntos de un conjunto dado. 

Supongamos por simplicidad que tenemos el conjunto cuyos elementos son los numeros del 1 al 3: $\{1, 2, 3\}$. Luego sus subconjuntos son $\emptyset, \{1\}, \{2\}, \{3\}, \{1, 2\}, \{1, 3\}, \{2, 3\}, \{1, 2, 3\}$.

Para ver la recursión hay que pensar en un argumento que nos proporcione una información útil. En este caso, los argumentos serán; el elemento $i$ no forma parte del subconjunto y el subconjunto que estamos generando. El caso base es cuando llegamos a revisar si añadir el $0$ que como no está en el conjunto original podemos imprimir el subconjunto formado.

Asi en cada llamada lo que hace la recursion es bifurar en dos mundos paralelos: uno en donde se añade el elemento que estamos viendo al subconjunto y otro en el que no. 

## Código

El código en python utilizando `listas` puede ser:

```python
def all_subset(n, subset):
  if n == 0:
    print(subset)
  else:
    all_subset(n-1, subset)
    all_subset(n-1, subset + [n])

all_subset(3, [])
```

El código en C++ utilizando `vector` puede ser:

```cpp
void all_subset(int n, vector<int>& subset) {
  if (n == 0) {
    print_subset(subset);
  }
  else {
    all_subset(n-1, subset);
    subset.push_back(n);
    all_subset(n-1, subset);
  }
}
```

Notese que se esta ocupando `vector<int>& subset` comoa argumento. Esto hace que no se tenga que copiar el vector en cada llamada, sino que se pasa por referencia y se modifica el mismo vector.
