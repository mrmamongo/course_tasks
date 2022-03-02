# brackets
Write a function that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it's invalid.

Необходимо написать функцию, которая принимает строку со скобками и показывает, является ли данная строка с последовательностью скобок сбалансированной.

Сбалансированной последовательностью скобок является такая последовательность, в которой все открывающие скобки имеют пару закрывающей скобки
### Функция
````c++
/*!
\param[in] str строка с последовательностью
\return является ли строка сбалансированной
*/
bool valid_parentheses(const std::string& str);
````

### Пример
```
() => true 
()()() => true
((((())))) => true
((() => false
)) => false
()(() => false
```
