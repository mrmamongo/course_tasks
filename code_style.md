## Оформление

* Пробелы после открывающей скобки и перед закрывающей скобкой не ставятся: f(1, (2 + 3)). Закрывающая скобка должна идти на той же строке, что и последнее выражение.
* Максимальная длина строки - 100 символов.
* Перед ; пробел не ставится. После ; в for ставится пробел.
* Пустые блоки записываются как {} (а не ;).
* Однострочные комментарии отделяются от кода двумя пробелами и начинаются с пробела.
* Пробелы в конце строки запрещены.
* Файл должен заканчиваться переводом строки.
* В range-base for двоеточие обрамляется пробелами.
* В начале/конце блока, после public/private/protected пустые строки не ставятся.
* Перед объявлением функции/структуры/класса - пустая строка обязательна.
* Секции include-ов и using-ов были упорядочены по алфавиту.

**Плохо:**
```cpp
#include <vector>
#include <iostream>
```
**Хорошо:**
```cpp
#include <iostream>
#include <vector>
```
**Плохо:**
```cpp
using std::vector;
using std::cin;
using std::cout;
```
**Хорошо:**
```cpp
using std::cin;
using std::cout;
using std::vector;
```
* Имя шаблона и параметр шаблона НЕ должны разделяться пробелом.

**Плохо:**
```cpp
vector <int> v;
```
**Хорошо:**
```cpp
vector<int> v;
```


## Именование

* Имена переменных должны начинаться со строчной буквы.

**Плохо**
```cpp
int Distance;
```
**Хорошо**
```cpp
int distance;
```

* Не используйте однобуквенных переменных (за исключением счётчиков циклов). Из названия переменной должно быть понятно что в ней хранится.

**Плохо**
```cpp
// количество строк и столбцов
size_t a, b;
```
**Хорошо**
```cpp
// количество строк и столбцов
size_t rowCount, columnCount;
```

* Не используйте транслит в именах.

**Плохо**
```cpp
size_t dlina_massiva;
```
**Хорошо**
```cpp
size_t length;
```

* Давайте переменным осмысленные имена. В частности, не используйте однобуквенных имён за исключением имён итераторов (i, j, k, ...), координат (x, y, z).

**Плохо**
```cpp
char alf(int j) { 
    ...
}
// или
char alphabet(int j) { 
    ...
}
```
```cpp
int ln; // длина
```
**Хорошо**
```cpp
char get_char(int j) {
    ...
}
```
```cpp
int length; // длина
``` 

* Для переменных-счётчиков не следует использовать имена `DocNum`, `NumDoc`, `DocsCount`, `DocsNum`, `CountDoc` из-за неграмотности и неоднозначности. Для числа элементов (скажем документов) можно использовать `NumDocs` или `DocCount`. Для функции, долго и явно подсчитывающей это число, подойдет `CountDocs()`.

* Функциям, которые возвращают `bool`, лучше давать имена, начинающиеся на `is` или `has`.

**Плохо**
```cpp
bool graph_connected() { ... }
bool element(int n) { ... }
```
**Хорошо**
```cpp
bool is_connected_graph() { ... }
bool has_element(int n) { ... }
```


## std::vector
* Если требуется создать вектор размера n, воспользуйтесь специальным конструктором.

**Плохо**
```cpp
vector<int> v;
v.resize(n);
```
**Хорошо**
```cpp
vector<int> v(n);
```   


## Циклы

* Если требуется перебрать элементы коллекции, предпочитайте *range-base for*. Он лаконичней и легче читается.

**Плохо**
```cpp
for (size_t i = 0; i < neighbors_list[vertex].size(); ++i) {
    if (!(visited[neighbors_list[vertex][i]])) {
        dfs(neighbors_list[vertex][i], visited);
    }
}
```
**Хорошо**
```cpp
for (const int& neighbor_vertex : neighbors_list[vertex]) {
    if (!(visited[neighbor_vertex])) {
        dfs(neighbor_vertex, visited);
    }
}
```


## Функции

Функции нужны:
1. для избежания дублирования кода;
1. для того, чтобы можно было их переиспользовать много раз в различных проектах.

* Порядок аргументов функции: сначала входные параметры (по значению либо константой ссылке), затем выходные.

* Передавайте аргументы в функции по константной ссылке везде, где это уместно.

**Плохо**
```cpp
void print_vector(vector<int> v) {
    ...
}
```
**Хорошо**
```cpp
void print_vector(const vector<int>& v) {
    ...
}
```

* Не создавайте функции с избыточным числом аргументов. Например, в функцию, печатающую вектор, не нужно передавать размер вектора.

**Плохо**
```cpp
void print_vector(const vector<int>& v, int n) {
    for (size_t i = 0; i < n; ++i) {
        cout << v[i] << " ";
    }
}
```
**Хорошо**
```cpp
void print_vector(const vector<int>& v) {
    // Используйте v.size(), чтобы получить длину вектора
    for (size_t i = 0; i < v.size(); ++i) {
        cout << v[i] << " ";
    }
}
```

* В проекте есть вектор, хранящий путь
```cpp
vector<int> way
```
и требуется написать функцию, которая печатает этот путь.

**Плохо**
```cpp
void print_way(const vector<int>& way) {
    for (int i : way) {
        cout << i << " ";
    }
}
```
**Хорошо**
```cpp
void print_vector(const vector<int>& v) {
    for (int i : v) {
        cout << i << " ";
    }
}
```
**Тоже хорошо**
```cpp
void print_vector(const vector<int>& v) {
    for (int i : v) {
        cout << i << " ";
    }
}

void print_way(const vector<int>& way) {
    print_vector(way);
}
```
Плохой вариант плох тем, что теряется свойство переиспользования у функции: вы не сможете использовать её в другом проекте, где, скажем, нужно будет распечатать вектор оценок.


## Прочее

* Необходимо явно подключать заголовочные файлы, в которых объявляются используемые функции/классы/... Запрещено явно подключать один и тот же заголовочный файл дважды.
* В качестве логических операторов следует использовать `&&`, `||`, ... Их аналоги `and`, `or`, ... запрещены.
* **Запрещено использовать** приведение типов в стиле СИ - следует использовать `*_cast`.
* Конструктор от одного аргумента должен быть объявлен `explicit`.
* При объявлении виртуальной функции следует использовать один и только один из спецификаторов `virtual`, `final`, `override`.
* При объявлении переменной спецификаторы `static`/`extern`/... идут **перед** именем типа.
* Везде, где это возможно, используйте префиксный инкремент и декремент.

**Плохо**
```cpp
i++;
it--;
```
**Хорошо**
```cpp
++i;
--it;
```
* Пишите код так, чтобы не было предупреждений (warnings) компилятора. Это нужно по двум причинам:
    1. Обычно компилятор выдаёт предупреждения по делу, на те места, где скрыта потенциальная ошибка.
    1. Если игнорировать "неважные" предупреждения, их может много накопиться и вы не заметите действительно важных.
* В частности, избегайте сравнений знаковых (int) и беззнаковых (size_t) переменных.

**Плохо**
```cpp
for (int i = 0; i < v.size(); ++i) {
    ...
}
```
**Хорошо**
```cpp
for (size_t i = 0; i < v.size(); ++i) {
    ...
}
```


## Спасибо
Инструкция взята [по ссылке](http://wiki.cs.hse.ru/%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B5_%D0%B7%D0%B0%D0%BD%D1%8F%D1%82%D0%B8%D1%8F_%D0%BF%D0%BE_%D0%BA%D1%83%D1%80%D1%81%D1%83_%D0%9E%D0%B8%D0%9C%D0%9F/C%2B%2B_check)