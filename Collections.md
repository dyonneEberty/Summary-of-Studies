```markdown
# Framework Collections em Java: List, Set e Map

## 📚 Por que esse conhecimento é crucial?

1. **Eficiência**: Escolher a estrutura de dados correta impacta diretamente no desempenho
2. **Manutenibilidade**: Código bem estruturado com collections apropriadas é mais fácil de manter
3. **Boas práticas**: Entender essas interfaces ajuda a escrever código mais idiomático
4. **Resolução de problemas**: Muitos desafios são sobre escolher a estrutura de dados certa

## 🗂️ Principais Interfaces e Implementações

### 1. List (Interface)
**Características**:
- ✅ Mantém ordem de inserção
- ✅ Permite elementos duplicados
- ✅ Acesso por índice

#### ArrayList
```java
List<String> arrayList = new ArrayList<>();
```
**Características**:
- 🏗️ Estrutura: Array dinâmico
- ⚡ Performance: Ótimo para acesso aleatório (`get()`)

**Métodos principais**:
```java
add(element), add(index, element)
get(index)
remove(index), remove(element)
set(index, element)
indexOf(element)
```

#### LinkedList
```java
List<String> linkedList = new LinkedList<>();
```
**Características**:
- ⛓️ Estrutura: Lista duplamente encadeada
- ⚡ Performance: Ótimo para inserções/remoções frequentes

**Métodos adicionais**:
```java
addFirst(), addLast()
getFirst(), getLast()
removeFirst(), removeLast()
```

### 2. Set (Interface)
**Características**:
- ❌ Não permite duplicados
- 🔀 Não mantém ordem (a menos que ordenado)

#### HashSet
```java
Set<String> hashSet = new HashSet<>();
```
**Características**:
- #️⃣ Estrutura: Tabela hash
- ⚡ Performance: O(1) para operações básicas

#### TreeSet
```java
Set<String> treeSet = new TreeSet<>();
```
**Características**:
- 🌳 Estrutura: Árvore rubro-negra
- 🔄 Mantém elementos ordenados

### 3. Map (Interface)
**Características**:
- 🔑 Armazena pares chave-valor
- 🚫 Chaves únicas

#### HashMap
```java
Map<String, Integer> hashMap = new HashMap<>();
```
**Características**:
- #️⃣ Estrutura: Tabela hash
- ⚡ Performance: O(1) para operações básicas

#### TreeMap
```java
Map<String, Integer> treeMap = new TreeMap<>();
```
**Características**:
- 🌳 Estrutura: Árvore rubro-negra
- 🔄 Mantém chaves ordenadas

## 🎯 Quando usar cada uma?

| Situação | Collection Recomendada |
|----------|-----------------------|
| Ordem importante + duplicatas | `ArrayList`/`LinkedList` |
| Elementos únicos + ordem não importa | `HashSet` |
| Elementos únicos + ordenados | `TreeSet` |
| Pares chave-valor + acesso rápido | `HashMap` |
| Pares chave-valor + ordenação | `TreeMap` |

## 💡 Dicas práticas

```java
// Inicialize com capacidade estimada
new ArrayList<>(100); 

// Crie listas imutáveis
Collections.unmodifiableList(lista);

// Para concorrência
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
```

## 🧪 Exercícios recomendados

1. Implemente um método que remove duplicatas de uma List
2. Crie um Map para contar frequência de palavras em um texto
3. Compare performance de contains() entre ArrayList e HashSet
4. Implemente um cache com LinkedHashMap (removendo os mais antigos)

## 📌 Exemplo Prático: Contador de Palavras

```java
public Map<String, Integer> contarPalavras(String texto) {
    Map<String, Integer> contador = new HashMap<>();
    String[] palavras = texto.split("\\s+");
    
    for (String palavra : palavras) {
        contador.put(palavra, contador.getOrDefault(palavra, 0) + 1);
    }
    
    return contador;
}
```


