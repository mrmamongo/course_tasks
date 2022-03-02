# fix_string_case

Необходимо написать функцию, которая принимает строку, регистры букв которой могут быть перемешаны. Данная функция должна преобразовать строку либо только в нижний регистр, либо только в верхний на основе следующих условий:
- преобразований должно быть минимальное количество
- если строка содержит одинаковое количество букв верхнего и нижнего регистра, конвертировать её в нижний регистр.

Также функция должна выводить в консоль примечание относительно того, что было сделано
````c++
fix_string_case("coDe") = "code". Lowercase characters > uppercase. Change only the "D" to lowercase.
fix_string_case("CODe") = "CODE". Uppercase characters > lowecase. Change only the "e" to uppercase.
fix_string_case("coDE") = "code". Upper == lowercase. Change all to lowercase.

````

### Функция
```c++
/*!
\param[in] str
\param[in] size размер массива
\return строка с исправленным регистром
*/
char* fix_string_case(const char* str);
```
