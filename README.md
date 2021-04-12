# Описание
Справочная информация по курсу JS фреймворка [React](https://www.udemy.com/course/react-the-complete-guide-incl-redux/)

# Оглавление
1. [Arrow Functions](#arrow-functions)
1. [Exports & Imports](#exports-&-imports)

# Arrow Functions
Варианты использования:

```javascript
// при отсутствии параметров
const print = () => {
    console.log('');
}
```

```javascript
// при использовании нескольких параметров
const print = (value, counter) => {
    console.log(counter + value);
}
```

```javascript
// при использовании только одного параметра
const print = counter => {
    console.log(value);
}
```

```javascript
// возврат значения
const multiply = number => number * 2;
```

# Exports & Imports
Разные типы экспорта и иморта модулей, функций и так далее.
persons.js
```javascript
const person = {
    name: 'Max'
}
export default person
```

utility.js
```javascript
export const clean = (smth) = {...};
export const baseData = 10;
```

app.js
```javascript
//обычный экспорт
import person from './person.js'
import prs from './person.js'

//именованный импорт
import {baseData} from './utility.js'
import {clean} from './utility.js'

//именованный импорт с переименовыванием
import {baseData as Base} from './utility.js'

// импорт всего содержимого как объекта
// переменные и функции будут доступны через точку (bundle.baseData)
import * as bundle from './utility.js'
```

# Classes
Класс - шаблон для объекта.

```javascript
class Person {
    name = 'Max' //свойство
    call = () => {/*some actions*/} //метод
}
```

Использование класса
```javascript
const myPerson = new Person();
myPerson.call();
console.log(myPerson.name);
```

Наследование
```javascript
class Person extends Master {
    
}
```

Пример класса и его использования

```javascript
class Human {
    constructor() {
        this.gender = 'male';
    }
    
    printGender () {
        console.log(this.gender);
    }
}

class Person extends Human {
    // метод запускающийся при создании экземпляра класса
    constructor() {
        super();// вызывает конструктор родительского класса
        this.name = 'Max';
        this.gender = null;
    }
    
    printName() {
        console.log(this.name);
    }
}

const person = new Person();
person.printName();
person.printGender();
```

## Пример класса на новом поколении ES6 / ES7

```javascript
class Human {
    gender = 'male';
    
    printGender = () => {
        console.log(this.gender);
    }
}

class Person extends Human {
    name = 'Max';
    gender = null;
    
    printName = () => {
        console.log(this.gender);
    }
}

const person = new Person();
person.printName();
person.printGender();
```

# Spread & Rest Operators

## Spread
`...` - берет **все** элменты старого массива и пишет в новый
```javascript
const newArray = [...oldArray, 1, 2];
const newObject = {...oldArray, newProp: 5};
```

## Rest
`...` - пишет **все** аргументы функции в массив, в последствии на массив можно
применять функции для работы с массивами
```javascript
sortArgs = (...args) => {
    return args.filter(el => el === 1);
}

console.log(sortArgs(1,2,3));
```

## Destructing
Позволяет извлекать **определенные (одиночные)** элементы массивов или свойства объектов для хранения в переменных.

### Array Destructing

```javascript
[a, b] = ['Hello', 'World'];
console.log(a);// Hello
console.log(b);// World

const number = [1, 2, 3];
[num1, ,num3] = numbers;
console.log(num1, num3); // 1 3
```

### Object Destructing

```javascript
{name} = {name: 'Max', age: 28};
console.log(name);// Max
console.log(age);// Undefined
```

# Reference and Primitive Types Refresher