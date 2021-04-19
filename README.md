# Описание

Справочная информация по курсу JS фреймворка [React](https://www.udemy.com/course/react-the-complete-guide-incl-redux/)

# Оглавление

1. [Arrow Functions](#arrow-functions)
1. [Exports & Imports](#exports-&-imports)

# Arrow Functions

Варианты использования:

```jsx
// при отсутствии параметров
const print = () => {
    console.log('');
}
```

```jsx
// при использовании нескольких параметров
const print = (value, counter) => {
    console.log(counter + value);
}
```

```jsx
// при использовании только одного параметра
const print = counter => {
    console.log(value);
}
```

```jsx
// возврат значения
const multiply = number => number * 2;
```

# Exports & Imports

Разные типы экспорта и импорта модулей, функций и так далее.

persons.js

```jsx
const person = {
    name: 'Max'
}
export default person
```

utility.js

```jsx
export const clean = (smth) = {...};
export const baseData = 10;
```

app.js

```jsx
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

```jsx
class Person {
    name = 'Max' //свойство
    call = () => {/*some actions*/
    } //метод
}
```

Использование класса

```jsx
const myPerson = new Person();
myPerson.call();
console.log(myPerson.name);
```

Наследование

```jsx
class Person extends Master {

}
```

Пример класса и его использования

```jsx
class Human {
    constructor() {
        this.gender = 'male';
    }

    printGender() {
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

```jsx
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

`...` - берет **все** элементы старого массива и пишет в новый

```jsx
const newArray = [...oldArray, 1, 2];
const newObject = {...oldArray, newProp: 5};
```

## Rest

`...` - пишет **все** аргументы функции в массив, в последствии на массив можно применять функции для работы с массивами

```jsx
sortArgs = (...args) => {
    return args.filter(el => el === 1);
}

console.log(sortArgs(1, 2, 3));
```

## Destructing

Позволяет извлекать **определенные (одиночные)** элементы массивов или свойства объектов для хранения в переменных.

### Array Destructing

```jsx
[a, b] = ['Hello', 'World'];
console.log(a);// Hello
console.log(b);// World

const number = [1, 2, 3];
[num1, , num3] = numbers;
console.log(num1, num3); // 1 3
```

### Object Destructing

```jsx
({name} = {name: 'Max', age: 28});
console.log(name);// Max
console.log(age);// Undefined
```

# Reference and Primitive Types Refresher

Примитивные типы данных:

- `string` Строки
- `number` Числа
- `boolean` Булево

При переназначении переменных, значение копируется.

```jsx
const number = 1;
const secondNumber = number;

console.log(secondNumber); // Prints 1
```

Ссылочные типы данных:

- `object` объекты
- `array` массивы

Объект хранится в памяти, но переменная `person` хранит в себе только указатель (ссылку)
на это место в памяти.

```jsx
const person = {
    name: 'Max'
}
const secondPerson = person;

console.log(secondPerson.name); // prints 'Max' 
```

По умолчанию, при переназначении переменной копируется указатель, а не значение.

```jsx
const person = {
    name: 'Max'
}
const secondPerson = person;

person.name = 'Manu'

console.log(secondPerson.name); // prints 'Manu' 
```

Выводит имя 'Manu', потому что переменная указывает на то же место в памяти, так как объект один.

Такая же история по умолчанию с массивами.

Для копирования объекта (создания нового) нужно использовать следующий синтаксис:

```jsx
const person = {
    name: 'Max'
}
const secondPerson = {
    ...person
};

person.name = 'Manu'

console.log(secondPerson.name); // prints 'Max' 
```

# Refreshing Array Functions

`.map()` - принимает на вход функцию и применяет ее к каждому элементу массива. Возвращает **новый** массив.

```jsx
const numbers = [1, 2, 3];
const doubleNumArray = numbers.map((num) => {
    return num * 2;
});

console.log(numbers); // [1, 2, 3];
console.log(doubleNumArray); // [2, 4, 6];
```

Другие полезные ссылки на функции применимые к массивам:

1. [`.find()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/find)
1. [`.findIndex()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/findIndex)
1. [`.filter()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/filter)
1. [`.reduce()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/reduce)
1. [`.concat()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/concat)
1. [`.slice()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/slice)
1. [`.splice()`](https://developer.mozilla.org/en-US/docs/Web/jsx/Reference/Global_Objects/Array/splice)

# Build Workflow

Лучшие практики для одно страничных и многостраничных веб приложений:

- Оптимизированный код
- Использование последних возможностей JS
- Использование пакетных менеджеров (менеджеров зависимостей) npm или yarn
- Использовать сборщик Webpack
- Использовать компилятор (Next Gen JS в обычный JS) Babel + Presets

# React Commands

`npm create-react-app <NAME> --scripts-version <VERSION>` - создает проект (папку)
с именем указанным в команде. `--scripts-version <VERSION>` - опционально, чем больше версия, тем больше новых
возможностей есть в React. Если не указывать, то будет задействована последняя версия скриптов.

`npm start` - запускает локальный сервер на localhost:3000

# React Common Features

## JSX

```jsx
    return (
    <div className="App">
        <h1>This is React Application.</h1>
    </div>
);
```

Пример указанный выше — то же самое что и пример указанный ниже. Так работает `jsx`.

```jsx
    return React.createElement('div', {className: 'App'},
    React.createElement('h1', null, 'This is React Application.'
    ));
```

## Props (properties)

Для использования свойств необходимо указать их в атрибутах компонента.

App.js

```jsx
<Person name="Ilya" age="23">My hobby: Nothing</Person>
```

Person.js

```jsx
const person = (props) => {
    return (
        <div>
            <p>I'm a {props.name} and I am {props.age} years old.</p>
            <p>{props.children}</p>
        </div>
    );
}
/**
 * Выведет:
 * I'm a Ilya and I am 23 years old.
 * My hobby: Nothing
 */
```

Свойства указанные в атрибутах, доступны через параметр `props.*`. Также есть свойства по умолчанию,
например `props.children`, в котором будет содержимое компонента переданное между `<Person>` и `</Person>`

## State

`state` - используется для изменения компонента внутри себя. Доступен только в компонентах основанных на классах (
class-based components).

```jsx
class NewPost extends Component { // state can only be accessed in class-based components!
    state = {
        counter: 1
    };

    render() { // Needs to be implemented in class-based components! Needs to return some JSX!
        return (
            <div>{this.state.counter}</div>
        );
    }
}
```

При изменении `state` компонент отобразит новые данные. Отличием `state` от `props` является то, что все происходит в
рамках одного компонента.
`state` не получает данные из вне (от родительских компонентов).
> `this.setState` в компонентах основанных на классах, при изменении
> совмещает данные старого объекта и нового

```jsx
state = {
    persons: [
        {name: 'Ilya', age: 23},
        {name: 'Vasyl', age: 25},
        {name: 'Peta', age: 30}
    ],
    otherState: 'value'
}

this.setState({
    persons: [
        {name: 'ILYAS', age: 18},
        {name: 'Vasyl', age: 18},
        {name: 'Peta', age: 18}
    ]
});
```

В результате в объекте `state` будет:

```jsx
state = {
    persons: [
        {name: 'ILYAS', age: 18},
        {name: 'Vasyl', age: 18},
        {name: 'Peta', age: 18}
    ],
    otherState: 'value'
}
```

## State в функциональных компонентах

```jsx
    const [personsState, setPersonsState] = useState({
    persons: [
        {name: 'Ilya', age: 23},
        {name: 'Vasyl', age: 25},
        {name: 'Peta', age: 30}
    ]
});
```

`personsState` - дает доступ к объекту `state`

`setPersonsState` - позволяет изменять содержимое объекта `state`

> `setPersonsState` не будет совмещать старый и новый объект, а просто перезапишет его
> на примере ниже потеряется свойство `otherState`

```jsx
    const [personsState, setPersonsState] = useState({
    persons: [
        {name: 'Ilya', age: 23},
        {name: 'Vasyl', age: 25},
        {name: 'Peta', age: 30}
    ],
    otherState: 'value'
});

const switchNameHandler = () => {
    setPersonsState({
        persons: [
            {name: 'ILYAS', age: 18},
            {name: 'Vasyl', age: 25},
            {name: 'Peta', age: 30}
        ]
    });
}
```

В результате в объекте `state` будет:

```jsx
state = {
    persons: [
        {name: 'ILYAS', age: 18},
        {name: 'Vasyl', age: 25},
        {name: 'Peta', age: 30}
    ]
}
```

**Свойства `otherState` больше нет в объекте `state`, так как оно не было указано при перезаписи объекта.**

Для удобства манипулирования объектами необходимо для каждого определять `useState`, например:

```jsx
    const [personsState, setPersonsState] = useState({
    persons: [
        {name: 'Ilya', age: 23},
        {name: 'Vasyl', age: 25},
        {name: 'Peta', age: 30}
    ]
});

const [otherState, setOtherState] = useState('value or object or array');
```

## React Hooks

Функции вида `useSomething` и есть **React Hooks**, например `useState`. Хуки позволяют добавлять функциональности к
функциональным компонентам.

## Stateful & Stateless components

Компоненты делятся на два вида:

- `stateful` компоненты с отслеживанием состояния (иначе они называются `smart` или `container`, так как содержат
  внутреннюю логику и функционал)
- `stateless` компоненты без отслеживания состояния (иначе они называются `dumb` (ввиду отсутствия внутренней логики)
  или `presentational` (потому что они только отображают данные))

Хорошей практикой является создавать как можно больше компонентов без отслеживания состояния. Так как приложения с
большим количеством `stateless` компонентов легче поддерживать, управлять, в них легко прослеживаются потоки данных,
четко понятны места основной логики приложения, распределения данных.

## Passing method references & parameters between components

Есть два способа использовать методы в дочерних компонентах:

- метод `.bind()` **(приоритетный вариант)**

```jsx
    <Person
    name={personsState.persons[1].name}
    age={personsState.persons[1].age}
    click={switchNameHandler.bind(this, 'ILYAS from BIND')}/>
```

- стрелочная функция **(может негативно влиять на производительность из-за слишком частого обновления данных)**

```jsx
  <Person
    name={personsState.persons[2].name}
    age={personsState.persons[2].age}
    click={() => switchNameHandler('ILYAS from arrow function')}/>
```

Если параметров нет, то можно просто передать ссылку на метод следующим образом:

```jsx
    <Person
    name={personsState.persons[1].name}
    age={personsState.persons[1].age}
    click={switchNameHandler}/>
```

## Two-way bonding

App.js

```jsx

const nameChangedHandler = (event) => {
    setPersonsState({
        persons: [
            {name: 'Ilya', age: 18},
            {name: event.target.value, age: 25},
            {name: 'Peta', age: 30}
        ]
    });
}

<Person
    name={personsState.persons[1].name}
    age={personsState.persons[1].age}
    click={switchNameHandler.bind(this, 'ILYAS from BIND')}
    changed={nameChangedHandler}
/>
```

Person.js

```jsx
const person = (props) => {
    return (
        <div>
            <p onClick={props.click}>I'm a {props.name} and I am {props.age} years old.</p>
            <p>{props.children}</p>
            <input type='text' onChange={props.changed} value={props.name}/>
        </div>
    );
}
```

Атрибут `changed` передает ссылку на метод

## Styling

Есть два способа стилизирования компонентов:

1. Создать файл `.css` в папке компонента, описать в нем стили и подключить к компоненту

```jsx
import './Person.css';
```

2. Описать стили как объект в компоненте (или отдельным файлом с последующим подключением через
   `import`) и использовать в атрибуте `style`

```jsx
    const style = {
    backgroundColor: 'white',
    font: 'inherit',
    border: '1px solid blue',
    padding: '8px',
    cursor: 'pointer'
}

<button
    style={style}
    onClick={() => switchNameHandler('ILYAS from arrow function')}>
    Switch Name
</button>
```

## Conditionals

Существует два способа создания условий:

1. В виде тернарного оператора

```jsx
const [state, setState] = useState({
    show: true
});

const toggleView = () => {
    const doesShow = state.show;
    setState({show: !state.show});
}

return (
    <button
        style={style}
        onClick={toggleView()}>
        Switch Name
    </button>
{
    state.show === true ?
        <div>
            <p>1</p>
            <p>2</p>
            <p>3</p>
        </div>
        : null
}
)
;
```

2. Через оператор `if()`

```jsx
const [state, setState] = useState({
    show: true
});

const toggleView = () => {
    const doesShow = state.show;
    setState({show: !state.show});
}

<button
    style={style}
    onClick={toggleView()}>
    Switch Name
</button>

let elements = null;

if (state.show) {
    elements = (
        <div>
            <p>1</p>
            <p>2</p>
            <p>3</p>
        </div>
    );
}

return (
    <button
        style={style}
        onClick={toggleView()}>
        Switch Name
    </button>
    {elements}
);
```

## Lists & keys

Таким способом выводится список данных

```jsx
<div>
    {personsState.persons.map((person, index) => {
        return (
            <Person
                name={person.name}
                age={person.age}
                key={index}
                changed={nameChangedHandler}
                click={() => deletePersonHandler(index)}>
                My hobby: Nothing
            </Person>
        );
    })}
</div>
```

Атрибут `key` должен обязательно должен присутствовать и быть уникальным, 
например `id` или как в этом случае - `index`

## Events

Основной список событий и примеров доступен в [документации по событиям](https://reactjs.org/docs/events.html).
