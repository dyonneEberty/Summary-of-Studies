# API de Data e Hora do Java: `LocalDate`, `LocalTime`, `LocalDateTime`, `OffsetTime`, `OffsetDateTime`

## 📅 Visão Geral

A partir do Java 8, foi introduzido o pacote `java.time` para substituir as antigas `Date` e `Calendar`. As principais classes são:

| Classe | Descrição | Exemplo |
|--------|-----------|---------|
| `LocalDate` | Data sem hora e fuso horário | 2025-06-18 |
| `LocalTime` | Hora sem data e fuso horário | 14:30:00 |
| `LocalDateTime` | Data e hora sem fuso horário | 2025-06-18T14:30:00 |
| `OffsetTime` | Hora com offset do fuso horário | 14:30:00-03:00 |
| `OffsetDateTime` | Data e hora com offset do fuso horário | 2025-06-18T14:30:00-03:00 |

## 🔍 Principais Classes

### 1. LocalDate
Representa uma data (ano-mês-dia) sem hora e sem fuso horário.

**Criação:**
```java
LocalDate hoje = LocalDate.now();
LocalDate dataEspecifica = LocalDate.of(2025, 6, 18);
LocalDate fromString = LocalDate.parse("2025-06-18");
```

**Métodos úteis:**
```java
hoje.getYear();       // 2025
hoje.getMonth();      // JUNE
hoje.getDayOfMonth(); // 18
hoje.plusDays(1);     // 2025-06-19
hoje.minusMonths(1);  // 2025-05-18
hoje.isLeapYear();    // false
```

### 2. LocalTime
Representa uma hora (hora-minuto-segundo-nanossegundo) sem data e sem fuso horário.

**Criação:**
```java
LocalTime agora = LocalTime.now();
LocalTime horaEspecifica = LocalTime.of(14, 30, 45);
LocalTime fromString = LocalTime.parse("14:30:45");
```

**Métodos úteis:**
```java
agora.getHour();     // 14
agora.getMinute();   // 30
agora.getSecond();   // 45
agora.plusHours(2);  // 16:30:45
agora.minusMinutes(15); // 14:15:45
agora.isBefore(LocalTime.NOON); // false
```

### 3. LocalDateTime
Combinação de `LocalDate` e `LocalTime`.

**Criação:**
```java
LocalDateTime agora = LocalDateTime.now();
LocalDateTime especifico = LocalDateTime.of(2025, 6, 18, 14, 30);
LocalDateTime fromString = LocalDateTime.parse("2025-06-18T14:30:00");
```

**Métodos úteis:**
```java
agora.toLocalDate(); // Retorna LocalDate
agora.toLocalTime(); // Retorna LocalTime
agora.plusDays(1).minusHours(3);
```

### 4. OffsetTime
`LocalTime` com offset (diferença do UTC).

**Criação:**
```java
OffsetTime agora = OffsetTime.now(); // Usa o fuso do sistema
OffsetTime especifico = OffsetTime.of(14, 30, 0, 0, ZoneOffset.ofHours(-3));
```

**Métodos úteis:**
```java
agora.getOffset(); // -03:00
agora.toLocalTime(); // Remove o offset
```

### 5. OffsetDateTime
`LocalDateTime` com offset (diferença do UTC).

**Criação:**
```java
OffsetDateTime agora = OffsetDateTime.now();
OffsetDateTime especifico = OffsetDateTime.of(2025, 6, 18, 14, 30, 0, 0, ZoneOffset.of("-03:00"));
```

**Métodos úteis:**
```java
agora.toInstant(); // Converte para Instant
agora.withOffsetSameInstant(ZoneOffset.UTC); // Converte para UTC
```

## ⚡ Quando usar cada uma?

| Cenário | Classe Recomendada |
|---------|--------------------|
| Somente data (ex: aniversários) | `LocalDate` |
| Somente hora (ex: horário de funcionamento) | `LocalTime` |
| Data e hora sem fuso (ex: alarme local) | `LocalDateTime` |
| Hora com fuso (ex: horário de voos) | `OffsetTime` |
| Data e hora com fuso (ex: transações globais) | `OffsetDateTime` |

## 🔄 Conversões entre classes

```java
// LocalDate + LocalTime = LocalDateTime
LocalDateTime ldt = LocalDate.now().atTime(LocalTime.now());

// LocalDateTime para LocalDate/LocalTime
LocalDate date = ldt.toLocalDate();
LocalTime time = ldt.toLocalTime();

// Adicionando offset
OffsetDateTime odt = ldt.atOffset(ZoneOffset.ofHours(-3));
```

## 📊 Comparação de Tempos

```java
LocalDate date1 = LocalDate.of(2025, 6, 18);
LocalDate date2 = LocalDate.of(2024, 12, 25);

date1.isAfter(date2);  // true
date1.isBefore(date2); // false
date1.isEqual(date2);  // false
```

## 💡 Boas Práticas

1. **Sempre use `java.time`** em vez de `Date` ou `Calendar`
2. **Para fusos horários específicos**, use `ZonedDateTime` (não abordado aqui)
3. **Para armazenamento**, converta para `Instant` (UTC)
4. **Formatação**:
   ```java
   DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm");
   String formatted = ldt.format(formatter);
   ```

## 🧪 Exercícios Práticos

1. Calcule a diferença entre duas datas em dias
2. Crie um método que verifica se uma data é fim de semana
3. Converta um `LocalDateTime` para o fuso horário de Tóquio
4. Implemente um validador de horário comercial (09:00-18:00)

## 📌 Exemplo: Diferença entre Datas

```java
LocalDate start = LocalDate.of(2025, 1, 1);
LocalDate end = LocalDate.of(2025, 6, 18);

long dias = ChronoUnit.DAYS.between(start, end); // 168 dias
```

> **Nota**: Documentação oficial: [Java Time Package](https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html)

[⬆ Voltar ao Topo](#api-de-data-e-hora-do-java)
``` 

### Dicas para GitHub:
1. Crie um arquivo chamado `java-time-api.md` no seu repositório
2. Adicione este conteúdo
3. Para melhor organização, você pode criar uma pasta `docs` ou `java` no seu repositório

O arquivo inclui:
- Tabelas comparativas
- Exemplos de código prontos para uso
- Recomendações de quando usar cada classe
- Exercícios práticos
- Links para documentação oficial
