# Consultas JPQL

## 🔸 Características

- Similar a SQL, pero opera sobre **entidades y atributos Java**, no tablas ni columnas.

- Se ejecutan con `EntityManager.createQuery()` o `createNamedQuery()`.

### Sintaxis básica

```Java
SELECT e FROM Empleado e WHERE e.nombre = :nombre
```

---

## 🔸 Cláusulas comunes

|Cláusula|Ejemplo|Descripción|
|---|---|---|
|`SELECT`|`SELECT c FROM Cliente c`|Selecciona entidades o atributos.|
|`WHERE`|`WHERE c.nombre LIKE :nom`|Condición de filtrado.|
|`JOIN`|`JOIN c.pedidos p`|Une entidades relacionadas.|
|`ORDER BY`|`ORDER BY c.nombre ASC`|Ordena resultados.|
|`GROUP BY`|`GROUP BY c.ciudad`|Agrupa resultados.|
|`HAVING`|`HAVING COUNT(p) > 3`|Filtra grupos.|

---

## 🔸 Funciones agregadas

`COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`

Ejemplo:

```Java
SELECT COUNT(p) FROM Pedido p WHERE p.total > 500
```

---

## 🔸 JOINs

|Tipo|Sintaxis|Uso|
|---|---|---|
|**INNER JOIN**|`JOIN c.pedidos p`|Devuelve solo los registros coincidentes.|
|**LEFT JOIN**|`LEFT JOIN c.pedidos p`|Incluye los que no tienen relación.|
|**FETCH JOIN**|`JOIN FETCH c.pedidos`|Carga las relaciones de forma inmediata.|

---

## 🔸 Named Queries

Declaradas en las entidades para ser reutilizadas.

```Java
@NamedQueries({
  @NamedQuery(name="Cliente.buscarTodos", query="SELECT c FROM Cliente c"),
  @NamedQuery(name="Cliente.buscarPorNombre", query="SELECT c FROM Cliente c WHERE c.nombre = :nombre")
})
```

Uso:

```Java
List<Cliente> lista = em.createNamedQuery("Cliente.buscarPorNombre", Cliente.class)
                        .setParameter("nombre", "Juan")
                        .getResultList();
```

---

## 🔸 Consultas dinámicas

```Java
Query q = em.createQuery("SELECT p FROM Pedido p WHERE p.total > :t");
q.setParameter("t", 1000);
List<Pedido> pedidos = q.getResultList();
```