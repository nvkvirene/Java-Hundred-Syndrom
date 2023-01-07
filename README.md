# Домашнее задание к занятию «Выстраивание процесса непрерывной интеграции»

##  Инструкция к выполнению домашнего задания

Перед тем как отправить своё решение на проверку преподавателю, сверьтесь с чеклистом.

<details>
  <summary> 1. В решении выполнены все требования задания</summary>

  Убедитесь, что все требования задания выполнены. Для этого перед отправкой внимательно прочтите весь текст условия задания и соотнесите сказанное в нём с вашим решением. Навык самопроверки работы перед ревью пригодится вам как при обучении, так и на работе.

  ---

</details>
<details>
   <summary>2. Правильно настроен Maven-проект, тесты проходят</summary>

  Репозиторий должен быть папкой вашего Мавен-проекта. Обратите внимание, что репозиторием не должна быть папка, в которой лежит папка Мавен-проекта, он сам должен быть папкой проекта. В нём должны быть соответствующие файлы и папки — `pom.xml`, `src` и другие.

  Не забудьте создать .gitignore-файл в корне проекта и добавить туда в игнорирование автогенерируемую папку `target`.

  Общая схема вашего `pom.xml`-файла:

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>ru.netology</groupId>
    <artifactId>НАЗВАНИЕ-ВАШЕГО-ПРОЕКТА-БЕЗ-ПРОБЕЛОВ</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>


    <dependencies>
        <dependency>
            ...
        </dependency>
        ...
    </dependencies>


    <build>
        <plugins>
            <plugin>
              ...
            </plugin>

            <plugin>
              ...
              <executions>
                <execution>
                  ...
                </execution>
                ...
              </executions>
            </plugin>
            ...
        </plugins>
    </build>

</project>
  ```

  #### JUnit
  Обратите внимание, что у артефакта нет `-api` на конце. Если у вас автоматически добавилась зависимость вида `<artifactId>junit-jupiter-api</artifactId>`, то лучше поменять артефакт на тот, что ниже, иначе будут сюрпризы в работе.

  ```xml
          <dependency>
              <groupId>org.junit.jupiter</groupId>
              <artifactId>junit-jupiter</artifactId>
              <version>5.7.0</version>
              <scope>test</scope>
          </dependency>
  ```

  #### Surefire
   Без этого плагина тесты могут Мавеном не запускаться, хоть в идее через кнопки они и будут проходить. Чтобы лишний раз убедиться, что всё работает, нажмите `Ctrl+Ctrl` и затем `mvn clean test`.

  ```xml
              <plugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-surefire-plugin</artifactId>
                  <version>2.22.2</version>
                  <configuration>
                      <failIfNoTests>true</failIfNoTests>
                  </configuration>
              </plugin>
  ```

  ---

</details>

<details>
   <summary> 3. Что делать, если возникли сложности </summary>

Это здорово. Если их преодолевать правильно, то можно получить большую образовательную пользу для себя. Периодическое возникновение вопросов, недопонимание пройденного материала — нормальная и неотъемлемая часть обучения. А мы здесь, чтобы помочь вам пройти этот путь.

  ### Что делать, если непонятна теория
  1. Если подобный вопрос разбирался на лекции, посмотрите ещё раз раздел с этой темой в видеозаписи.
  1. Если вопрос не решился, попробуйте поискать ответ самостоятельно в интернете, этот навык пригодится вам в работе.
  1. Если самостоятельно разобраться не удалось, задайте вопрос в общем чате, мы обязательно поможем.

  ### Что делать, если непонятно условие задания
  1. Прежде чем задать вопрос по условию задачи, перечитайте его ещё раз и убедитесь, что в тексте условия нет прямого ответа на этот вопрос. Умение работать с текстом — важный навык работы с информацией.
  1. Если ответа на свой вопрос в тексте условия не увидели, задайте его в общем чате, мы раскроем детали условия.

  ### Что делать, если не получается задача
Если ваша проблема — это **ошибка компиляции** — подчёркивает красным, не даёт запустить программу, сборки проекта, CI и прочие подобные ошибки, то:
  1. Найдите и прочитайте текст ошибки, который вам подсвечивает идея или логи. «Подчёркивает красным» — это не описание ошибки.
  1. Попробуйте понять текст ошибки, при необходимости воспользуйтесь переводчиком. Не страшно, если вы переведёте неточно, тут главное — сам процесс: со временем и с нашей помощью вы будете это делать лучше и лучше, но, пропуская этот этап, вы не сможете научиться это делать.
  1. Если не получилось понять ошибку по её тексту, попробуйте её загуглить и изучить подобную ошибку у других людей. Попробуйте примерить решения их проблем на свой код. Соотнесите найденные описания ошибки с пройденной теорией.
  1. Если всё равно ваши трудности не разрешились, напишите в общий чат, обязательно указав:
      1. название задачи и ссылку на условие;
      1. ссылку на вашу работу;
      1. текст и скриншот, не фотографию, ошибки;
      1. ваши размышления и описание шагов, которые вы совершили для решения.

Если ваша проблема — это **ошибка исполнения**, программа умирает уже после запуска, или она **отрабатывает неправильно**, из-за чего ваши тесты не проходят, то:
  1. Воспользуйтесь отладчиком для пошагового анализа работы вашей программы. Так вы или убедитесь в неправильности придуманного вами алгоритма, или найдёте конкретное место, где ожидаемое поведение программы разошлось с фактическим.
  1. Если проблему найти не получилось, напишите в общий чат, обязательно указав:
      1. название задачи и ссылку на условие;
      1. ссылку на вашу работу;
      1. конкретное и подробное описание проблемы или затруднения при решении задачи. «Помогите, что-то не так» — это не описание;
      1. подробное описание вашего анализа программы с помощью отладчика вместе со скринами;
      1. ваши размышления и описание шагов, которые вы совершили для решения.
  ---

</details>

<details>
  <summary>4. Отформатирован код [:warning:: в этом задании форматировать нужно только код тестов]</summary>

  Кроме правил, нарушение которых приводит к ошибкам компиляции, есть ещё и [правила форматирования кода](https://google.github.io/styleguide/javaguide.html), соблюдение которых обязательно при написании программ.

С большинством проблем может справиться автоформатирование в идее. Для этого выберите `Code -> Reformat code` в меню или используйте горячие сочетания клавиш. В меню будет показано актуальное сочетание для вашей операционной системы. Так, идея поправит неправильные отступы, пробелы и некоторые другие ошибки. Следите, чтобы у `if-else`, `for`, `while` всегда были `{}`.

  Проблемы с именованием сущностей нужно решать самим. Так, все ячейки, кроме `final`-констант, и методы должны писаться [камелкейсом](https://ru.wikipedia.org/wiki/CamelCase) с **маленькой** буквы, а классы и интерфейсы — камелкейсом с **большой** буквы.

  Мы вам настоятельно советуем всегда держать код в отформатированном виде во время разработки, со временем глаз привыкнет, и вы почувствуете, насколько это облегчает поиск ошибок в коде и его анализ. В любом случае перед отправкой кода на проверку его обязательно нужно отформатировать, иначе он может быть отправлен на доработку без более глубокой проверки на этой итерации.
</details>

<details open>
  <summary>5. Настроен Github CI с verify-сборкой Maven и JaCoCo :new:</summary>

  #### CI
  После связывания локального репозитория с удалённым и первого пуша в заготовки проекта, время настроить CI на основе GitHub Actions. Шаблон вашего maven.yml должен выглядеть вот так, убедитесь, что всё совпадает с вашим шаблоном, например, что вы указали фазу `verify`, а не `package`:
  ```yml
  name: Java CI with Maven
  on: [push, pull_request]
  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Build with Maven
        run: mvn -B -e verify
  ```

  #### JaCoCo

  ```xml
              <plugin>
                  <groupId>org.jacoco</groupId>
                  <artifactId>jacoco-maven-plugin</artifactId>
                  <version>0.8.5</version>
                  ...
  ```

  Инициализация:
  ```xml
                      <execution>
                          <id>prepare-agent</id>
                          <goals>
                              <goal>prepare-agent</goal>
                          </goals>
                      </execution>
  ```

  В режиме генерации отчётов:
  ```xml
                      <execution>
                          <id>report</id>
                          <phase>verify</phase>
                          <goals>
                              <goal>report</goal>
                          </goals>
                      </execution>
  ```

  В режиме проверки и обрушения сборки по уровню покрытия:
  ```xml
                      <execution>
                          <id>check</id>
                          <goals>
                              <goal>check</goal>
                          </goals>
                          <configuration>
                              <rules>
                                  <rule>
                                      <limits>
                                          <limit>
                                              <counter>LINE</counter>
                                              <value>COVEREDRATIO</value>
                                              <minimum>100%</minimum>
                                          </limit>
                                      </limits>
                                  </rule>
                              </rules>
                          </configuration>
                      </execution>
  ```

</details>

# Задание 1. Синдром 100% (обязательное к выполнению)

Вы попали в команду максималистов, которые хотят, чтобы те автотесты, которые вы пишете, покрывали код на 100%.

Но вот незадача:
* непонятно, что такое 100%;
* непонятно, как это сделать.

Вспоминаем: покрытием кода у нас занимается JaCoCo, но он просто сигнализирует о том, что конкретно пошло не так.

Большинство подобных плагинов, помимо целей отчётности (`report`), содержат ещё цель `check`, которая обрушает сборку, если не выполнены определённые проверки.

Что вам нужно
1. Создать Мавен-проект с тестируемым кодом из листинга кода, он указан ниже по условию.
1. Изучить [документацию на плагин](https://www.eclemma.org/jacoco/trunk/doc/maven.html), а конкретно — на цель `check`.
1. Внедрить эту цель во фазу `verify`. Обратите внимание, что эта цель и так публикуется в эту фазу.
1. Настроить правила по покрытию на 100%. При этом нужно изучить разницу между счётчиками `INSTRUCTION`, `LINE`, `BRANCH`, `COMPLEXITY`.
1. Вникнуть в тестируемый код.
1. Выбрать один из счётчиков и добиться 100% покрытия через добавление новых тестов.

**Важно**: использовать можно только один из следующих: 
1. `INSTRUCTION`
1. `LINE`
1. `BRANCH`

Обратите внимание на чеклист в начале условия, он содержит подсказки по внедрению JaCoCo в ваш Мавен-проект.

Тестируемый код, его как-либо редактировать **нельзя**:
```java
package ru.netology.statistic;
public class StatisticsService {
  /**
   * Calculate index of max income
   *
   * @param incomes - array of incomes
   * @return - index of first max value
   */
  public long findMax(long[] incomes) {
    long current_max_index = 0;
    long current_max = incomes[0];
    for (long income : incomes)
      if (current_max < income)
        current_max = income;
        return current_max;
  }
}
```

Класс с тестами, его надо будет расширить новыми тестами:
```java
package ru.netology.statistic;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;
public class StatisticsServiceTest {
  @Test
  void findMax() {
    StatisticsService service = new StatisticsService();
    long[] incomesInBillions = {12, 5, 8, 4, 5, 3, 8, 6, 11, 11, 12};
    long expected = 12;
    long actual = service.findMax(incomesInBillions);
    assertEquals(expected, actual);
  }
}
```

Итого: отправьте на проверку ссылку на репозиторий GitHub с вашим проектом.
