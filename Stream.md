# API Stream em Java - Material de Estudo

## 📌 Introdução
A API Stream, introduzida no Java 8, revolucionou o processamento de coleções com uma abordagem funcional.

## 🔍 Importância
- **Código mais limpo**: Redução de boilerplate
- **Processamento declarativo**: Foco no "o quê" em vez do "como"
- **Paralelismo fácil**: `.parallelStream()` para operações paralelas
- **Pipeline de operações**: Encadeamento natural de métodos
- **Lazy evaluation**: Otimização de performance

## 🛠️ Componentes Principais
1. **Fonte**: Coleções, arrays, geradores
2. **Operações intermediárias**: Transformam o stream
3. **Operações terminais**: Produzem resultado final

## 📋 Operações Intermediárias (Lazy)
| Operação       | Exemplo                          | Descrição                     |
|----------------|----------------------------------|-------------------------------|
| `filter()`     | `.filter(n -> n > 5)`           | Filtra elementos              |
| `map()`        | `.map(String::toUpperCase)`     | Transforma elementos          |
| `sorted()`     | `.sorted(Comparator.reverse())` | Ordena elementos              |
| `distinct()`   | `.distinct()`                   | Remove duplicados             |
| `limit()`      | `.limit(10)`                    | Limita quantidade de elementos|

## 🎯 Operações Terminais (Eager)
| Operação       | Exemplo                          | Saída               |
|----------------|----------------------------------|---------------------|
| `forEach()`    | `.forEach(System.out::println)`  | Efeito colateral    |
| `collect()`    | `.collect(Collectors.toList())`  | Coleção             |
| `reduce()`     | `.reduce(0, Integer::sum)`       | Valor único         |
| `count()`      | `.count()`                       | long (quantidade)   |
| `anyMatch()`   | `.anyMatch(s -> s.contains("a"))`| boolean             |

## ⚠️ Particularidades
1. **Single-use**: Streams não podem ser reutilizados
2. **Lazy**: Operações só executam com terminal
3. **Paralelismo**: Cuidado com operações stateful
4. **Imutabilidade**: Não alteram a fonte original

## 💡 Exemplos Práticos

### Filtro e Transformação
```java
List<String> result = lista.stream()
                         .filter(s -> s.length() > 3)
                         .map(String::toUpperCase)
                         .collect(Collectors.toList());
```

### Agrupamento
```java
Map<String, List<Pessoa>> porCidade = pessoas.stream()
                                           .collect(groupingBy(Pessoa::getCidade));
```

### Paralelismo
```java
int soma = numeros.parallelStream()
                .filter(n -> n % 2 == 0)
                .mapToInt(n -> n)
                .sum();
```

## ✅ Quando Usar
- Processamento complexo de coleções
- Operações que beneficiam de paralelismo
- Código mais declarativo

## ❌ Quando Evitar
- Operações simples (um loop resolve)
- Quando precisa de acesso aleatório
- Controle preciso de iteração

## 📚 Boas Práticas
- Prefira métodos referência (`String::length`)
- Use `Collectors` estáticos para operações comuns
- Atente para operações stateful em paralelo
- Documente pipelines complexas

## 🔄 Comparação Tradicional vs Stream
**Tradicional**:
```java
List<String> result = new ArrayList<>();
for(String s : lista) {
    if(s.length() > 3) {
        result.add(s.toUpperCase());
    }
}
```

**Stream**:
```java
List<String> result = lista.stream()
                        .filter(s -> s.length() > 3)
                        .map(String::toUpperCase)
                        .collect(Collectors.toList());
```

## 🏁 Conclusão
A API Stream oferece uma forma moderna e eficiente de processar coleções em Java, combinando elegância sintática com poder de processamento.
```
