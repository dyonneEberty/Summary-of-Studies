# Generics em Java - Material de Estudo

## 📌 Introdução
Generics foram introduzidos no Java 5 para fornecer **type safety** e eliminar a necessidade de casts explícitos em coleções.

## 🔍 Importância
- **Segurança de tipos**: Detecta erros em tempo de compilação
- **Reúso de código**: Classes/métodos que trabalham com vários tipos
- **Eliminação de casts**: Redução de boilerplate code
- **Performance**: Evita overhead de boxing/unboxing

## 🛠️ Conceitos Fundamentais

### 1. Classes Genéricas
```java
public class Caixa<T> {
    private T conteudo;
    
    public void guardar(T item) {
        this.conteudo = item;
    }
    
    public T pegar() {
        return conteudo;
    }
}
```

### 2. Métodos Genéricos
```java
public <T> void imprimirArray(T[] array) {
    for(T elemento : array) {
        System.out.println(elemento);
    }
}
```

### 3. Interfaces Genéricas
```java
public interface Repositorio<T, ID> {
    void salvar(T entidade);
    T buscarPorId(ID id);
}
```

## 📋 Características Principais

### Type Parameters Comuns
- `E` - Element (usado em coleções)
- `K` - Key
- `V` - Value
- `T` - Type
- `N` - Number

### Wildcards
| Tipo           | Sintaxe      | Descrição                          |
|----------------|--------------|------------------------------------|
| Unbounded      | `<?>`        | Qualquer tipo                      |
| Upper bounded  | `<? extends Number>` | Tipos que herdam de Number |
| Lower bounded  | `<? super Integer>`  | Tipos pai de Integer      |

## ⚠️ Restrições Importantes
1. **Não pode usar primitivos**: `List<int>` → Use `List<Integer>`
2. **Não pode instanciar tipos**: `new T()` → Erro de compilação
3. **Não pode usar em arrays**: `T[] array = new T[10];` → Erro
4. **Não funciona com instanceof**: `obj instanceof List<String>` → Erro

## 💡 Exemplos Práticos

### Classe Genérica
```java
public class Par<K, V> {
    private K chave;
    private V valor;
    
    // construtor, getters, setters
}
```

### Método com Wildcard
```java
public void imprimirLista(List<?> lista) {
    for(Object item : lista) {
        System.out.println(item);
    }
}
```

### Herança com Generics
```java
public class NumericBox<T extends Number> {
    private T numero;
    
    public double getDoubleValue() {
        return numero.doubleValue();
    }
}
```

## ✅ Vantagens
- **Type safety** em tempo de compilação
- **Código mais limpo** sem casts desnecessários
- **Maior abstração** no design de APIs
- **Reúso de código** para múltiplos tipos

## ❌ Limitações
- Aumenta um pouco a complexidade do código
- Algumas operações são restritas (como criação de instâncias)
- Pode causar "type erasure" warnings

## 🔄 Comparação Sem/Com Generics

**Sem Generics**:
```java
List lista = new ArrayList();
lista.add("texto");
String s = (String) lista.get(0); // Cast necessário
```

**Com Generics**:
```java
List<String> lista = new ArrayList<>();
lista.add("texto");
String s = lista.get(0); // Sem cast
```

## 🏁 Conclusão
Generics são essenciais para:
- Criar código mais seguro e expressivo
- Desenvolver coleções e APIs flexíveis
- Evitar erros de ClassCastException
- Promover reúso de código mantendo type safety

## 📚 Melhores Práticas
1. Use sempre que possível em coleções
2. Prefira interfaces genéricas (List<E> em vez de List)
3. Documente bem os tipos genéricos complexos
4. Utilize wildcards para maior flexibilidade em métodos
```
