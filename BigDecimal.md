```markdown
# Classe `BigDecimal` em Java

## 📌 Importância

A classe `BigDecimal` é essencial para:

- Resolver problemas de arredondamento dos tipos `float` e `double`
- Fornecer precisão arbitrária em cálculos numéricos
- Garantir exatidão em operações financeiras (onde centavos importam!)

## 🎯 Cenários de Uso Principais

1. **Sistemas financeiros** (cálculos monetários, juros, investimentos)
2. **Aplicações científicas** que exigem alta precisão
3. **Cálculos fiscais e tributários**
4. **Qualquer sistema onde a precisão decimal é crítica**

## 🛠️ Principais Métodos

### Construção de Objetos

```java
// Forma recomendada (usando String)
BigDecimal valor1 = new BigDecimal("123.45");

// Método preferido para literais double
BigDecimal valor2 = BigDecimal.valueOf(123.45);

// NÃO RECOMENDADO (pode ter problemas de precisão)
BigDecimal valor3 = new BigDecimal(123.45);
```

### Operações Básicas

| Operação | Método | Exemplo |
|----------|--------|---------|
| Soma | `add()` | `a.add(b)` |
| Subtração | `subtract()` | `a.subtract(b)` |
| Multiplicação | `multiply()` | `a.multiply(b)` |
| Divisão | `divide()` | `a.divide(b, escala, arredondamento)` |

### Exemplo de Operações

```java
BigDecimal a = new BigDecimal("10.50");
BigDecimal b = new BigDecimal("3.20");

// Soma
BigDecimal soma = a.add(b); // 13.70

// Divisão com arredondamento
BigDecimal divisao = a.divide(b, 4, RoundingMode.HALF_UP); // 3.2812
```

### Comparação de Valores

```java
// Use compareTo() (retorna -1, 0 ou 1)
int resultado = a.compareTo(b);

// EVITE equals() para comparação numérica
// pois 2.0 não é igual a 2.00 para equals()
```

### Controle de Escala e Arredondamento

```java
BigDecimal valor = new BigDecimal("123.456789");

// Definir casas decimais
BigDecimal arredondado = valor.setScale(2, RoundingMode.HALF_UP); // 123.46

// Obter escala atual
int casasDecimais = valor.scale(); // 6
```

## ✅ Boas Práticas

1. **Prefira `String` ou `valueOf()` na construção**
2. **Sempre defina escala e arredondamento em divisões**
3. **Use `compareTo()` para comparações numéricas**
4. **Para valores monetários, use escala 2**
5. **Considere `MathContext` para operações complexas**

## 💻 Exemplo Completo

```java
import java.math.BigDecimal;
import java.math.RoundingMode;

public class CalculoFinanceiro {
    public static void main(String[] args) {
        BigDecimal preco = BigDecimal.valueOf(9.99);
        BigDecimal quantidade = new BigDecimal("3.5");
        
        BigDecimal total = preco.multiply(quantidade)
                               .setScale(2, RoundingMode.HALF_UP);
        
        System.out.println("Total: R$ " + total); // Total: R$ 34.97
    }
}
```

## ⚠️ Cuidados Importantes

- Nunca use construtores com `double` para valores exatos
- Atente-se aos modos de arredondamento:
  - `RoundingMode.HALF_UP` (arredonda para cima a partir de 0.5)
  - `RoundingMode.HALF_EVEN` (arredondamento bancário)
- `BigDecimal` é imutável - operações retornam novos objetos

## 📚 Material Complementar

- [Documentação Oficial BigDecimal](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html)
- [Tutorial Oracle sobre números](https://docs.oracle.com/javase/tutorial/java/data/numberclasses.html)
``` 

Você pode salvar este conteúdo como `bigdecimal_java.md` e subir para seu GitHub. O formato Markdown torna a leitura mais organizada e facilita a consulta rápida quando você estiver estudando.
