#Homework 3 

###Задача 1  
Напишите функцию sum, которая будет работать как показано в примере ниже: 
```
function sum(a) {

  var currentSum = a;

  function f(b) {
    currentSum += b;
    return f;
  }

  f.toString = function() {
    return currentSum;
  };

  return f;
}
sum(1)(2) == 3; // 1 + 2
sum(1)(2)(3) == 6; // 1 + 2 + 3
sum(5)(-1)(2) == 6
sum(6)(-1)(-2)(-3) == 0
sum(0)(1)(2)(3)(4)(5) == 15
```
Количество скобок может быть любым. 

###Задача 2  
Напишите функцию runString, которая: 

1)принимает 2 аргумента:
 * arg:  аргумент любого типа
 * объект со свойствами:
1. param: строка.
2. func: строка, содержащая код функции. 

2)выполняет код функции func, переданной ей в качестве аргумента, с параметром arg. 
Например: 
```
var arg = 4,                         // аргумент для функции runString
    obj = {
      param: 'num',                  // имя параметра для функции в свойстве func
      func: 'return Math.sqrt(num)'  // функция, которая должна быть вызванв с  агрументом arg
    };

runString(arg, obj)              
``` 

### Задача 3. 
 Дан объект ladder 
```
var ladder = {
  step: 0,
  up: function() { // вверх по лестнице
    this.step++;
  },
  down: function() { // вниз по лестнице
    this.step--;
  },
  showStep: function() { // вывести текущую ступеньку
    alert( this.step );
  }
};
```
Сейчас, для последовательного вызова нескольких методов объекта, нужно вызывать каждый из них отдельно:
```
ladder.up();
ladder.up();
ladder.down();
ladder.showStep(); // 1 
```
Модифицируйте код методов объекта, чтобы вызовы можно было делать цепочкой:
```
ladder.up().up().down().up().down().showStep(); // 1
```
```
var ladder = {
  step: 0,
  up: function() { 
    this.step++;
    return this;
  },
  down: function() { 
    this.step--;
     return this;
  },
  showStep: function() { 
    alert( this.step );
     return this;
  }
};
ladder.up().up().down().up().down().showStep()
```