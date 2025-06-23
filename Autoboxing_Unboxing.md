# Autoboxing e Unboxing em Java

## 📌 Conceitos Básicos

**Autoboxing** e **Unboxing** são recursos introduzidos no Java 5 que permitem a conversão automática entre tipos primitivos e seus respectivos wrappers (classes objeto equivalentes).

### 🔄 Autoboxing
Conversão automática de tipo primitivo → wrapper correspondente:

```java
int primitivo = 42;
Integer wrapper = primitivo; // Autoboxing
```

### 🔄 Unboxing
Conversão automática de wrapper → tipo primitivo correspondente:

```java
Integer wrapper = Integer.valueOf(42);
int primitivo = wrapper; // Unboxing
```

## ✅ Boas Práticas

### 1. Prefira tipos primitivos quando possível
- **Wrappers** consomem mais memória e têm overhead
- **Ruim**: `Integer soma = 0;`
- **Bom**: `int soma = 0;`

### 2. Cuidado com comparações
```java
Integer a = 100;
Integer b = 100;
a == b; // true (cache de -128 a 127)

Integer c = 200;
Integer d = 200;
c == d; // false (fora do cache)
```
👉 **Sempre use `.equals()` para wrappers**

### 3. Atenção a NullPointerException
```java
Integer valor = null;
int primitivo = valor; // 💥 NullPointerException
```

### 4. Performance em loops
Evite em operações repetitivas:

```java
// ⚠️ Ruim (autoboxing em cada iteração)
Long soma = 0L;
for(long i = 0; i < 1_000_000; i++) {
    soma += i;
}

// ✅ Bom
long soma = 0L;
for(long i = 0; i < 1_000_000; i++) {
    soma += i;
}
```

### 5. Uso correto em Collections
```java
List<Integer> numeros = new ArrayList<>();
numeros.add(1); // Autoboxing (int → Integer)
int num = numeros.get(0); // Unboxing (Integer → int)
```

## 🏁 Quando usar Wrappers?

| Caso de Uso | Exemplo |
|-------------|---------|
| Armazenar em Collections | `List<Integer>` |
| Representar valores nulos | `Integer idade = null` |
| APIs que exigem objetos | Reflexão, JPA |
| Genéricos | `Class<Integer>` |

## ⚠️ Cuidados Importantes

- **Cache de valores**: Wrappers entre -128 e 127 são cacheados
- **Overhead**: Operações matemáticas com wrappers são mais lentas
- **NPE**: Primitivos nunca são null, wrappers podem ser

## 🔍 Exemplo Completo

```java
public class AutoboxingExample {
    public static void main(String[] args) {
        // Autoboxing
        List<Integer> lista = new ArrayList<>();
        lista.add(10); // int → Integer
        
        // Unboxing
        int valor = lista.get(0); // Integer → int
        
        // Cuidado com null!
        Integer possivelNull = buscarIdade();
        if(possivelNull != null) {
            int idade = possivelNull; // Safe unboxing
        }
    }
    
    private static Integer buscarIdade() {
        return null; // Simulando valor potencialmente nulo
    }
}
```

📚 **Dica Final**: Use primitivos por padrão e wrappers apenas quando necessário!
