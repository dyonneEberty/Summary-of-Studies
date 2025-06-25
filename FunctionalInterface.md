# Interfaces Funcionais em Java

## 📌 O que são Interfaces Funcionais?

Interfaces funcionais são **interfaces que contêm apenas um método abstrato**. Elas são a base da programação funcional em Java, introduzida principalmente a partir do Java 8.

```java
@FunctionalInterface
interface Calculadora {
    int operacao(int a, int b); // único método abstrato
}
```

## � Problemas que Resolvem

1. **Verbose de classes anônimas**:
   - Antes do Java 8, era necessário criar classes anônimas completas para pequenos comportamentos

```java
// Jeito antigo (pré-Java 8)
button.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent e) {
        System.out.println("Botão clicado!");
    }
});
```

2. **Acoplamento desnecessário**:
   - Implementações simples exigiam classes separadas

3. **Dificuldade em passar comportamentos como parâmetros**

## 💡 Importância

1. **Habilitam programação funcional** em Java
2. **Permitem expressividade** com lambdas
3. **Reduzem código boilerplate**
4. **Facilitam APIs mais flexíveis**

## 🎯 Quando Usar?

1. **Quando precisar passar comportamentos como parâmetros**
   ```java
   lista.forEach(item -> System.out.println(item));
   ```

2. **Para implementações simples e descartáveis**
   ```java
   Thread t = new Thread(() -> System.out.println("Nova thread!"));
   ```

3. **Em operações de stream**
   ```java
   lista.stream()
        .filter(n -> n % 2 == 0)
        .map(n -> n * 2)
        .forEach(System.out::println);
   ```

## 📚 Principais Interfaces Funcionais do Java

| Interface           | Método           | Descrição                          | Exemplo de Lambda           |
|---------------------|------------------|------------------------------------|-----------------------------|
| `Function<T,R>`     | `R apply(T t)`   | Transforma um valor em outro       | `x -> x * 2`                |
| `Predicate<T>`      | `boolean test(T)`| Testa uma condição                 | `s -> s.length() > 5`       |
| `Consumer<T>`       | `void accept(T)` | Consome um valor sem retorno       | `x -> System.out.println(x)`|
| `Supplier<T>`       | `T get()`        | Fornece valores                    | `() -> new Random().nextInt()`|
| `Runnable`          | `void run()`     | Executa uma ação                   | `() -> System.out.println("Hi")`|

## 🔄 Comparação: Antes e Depois do Java 8

**Antes (Classe Anônima):**
```java
Collections.sort(lista, new Comparator<String>() {
    @Override
    public int compare(String s1, String s2) {
        return s1.length() - s2.length();
    }
});
```

**Depois (Lambda):**
```java
Collections.sort(lista, (s1, s2) -> s1.length() - s2.length());
```

## 🏆 Melhores Práticas

1. **Use `@FunctionalInterface`** para documentar sua intenção
   ```java
   @FunctionalInterface
   interface Validador {
       boolean validar(String texto);
   }
   ```

2. **Prefira lambdas** sobre classes anônimas para implementações simples

3. **Use method references** quando possível
   ```java
   lista.forEach(System.out::println);
   ```

4. **Combine com Streams** para operações em coleções

## ⚠️ Cuidados e Limitações

1. **Só pode ter um método abstrato** (mas pode ter métodos default)
2. **Variáveis locais usadas em lambdas devem ser final ou efetivamente final**
3. **Não substituem OOP em todos os casos** - use com critério

## 🧠 Exercício Prático

Implemente uma calculadora usando interfaces funcionais:

```java
public class Calculadora {
    public static void main(String[] args) {
        Operacao soma = (a, b) -> a + b;
        Operacao subtrai = (a, b) -> a - b;
        
        System.out.println(soma.executar(5, 3)); // 8
        System.out.println(subtrai.executar(5, 3)); // 2
    }
}

@FunctionalInterface
interface Operacao {
    int executar(int a, int b);
}
```

## 📌 Resumo Final

- **Para que servem**: Simplificar implementações de comportamentos únicos
- **Quando usar**: Passar lógica como parâmetro, implementações simples
- **Vantagens**: Código mais conciso, legível e funcional
- **Desvantagens**: Curva de aprendizado, não substitui OOP complexa

> **Dica**: Domine as 4 principais interfaces (`Function`, `Predicate`, `Consumer`, `Supplier`) pois elas cobrem 80% dos casos de uso!
``` 

Este arquivo Markdown contém:
- Explicação conceitual clara
- Exemplos de código realçados
- Tabela de interfaces principais
- Comparação antes/depois do Java 8
- Exercício prático
- Destaques e boxes importantes
- Emojis para melhor navegação visual

Perfeito para estudos e revisão de conceitos de Java! Você pode salvar como `interfaces-funcionais.md` no seu GitHub.
