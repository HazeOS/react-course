# Описание

Справочная информация по курсу JS фреймворка [React](https://www.udemy.com/course/react-the-complete-guide-incl-redux/)

# Оглавление

1. [Arrow Functions](#arrow-functions)
1. [Exports & Imports](#exports-&-imports)
1. [Classes](#classes)
   - [Class example](#class-example-ES6-/-ES7)
1. [Spread & Rest Operators](#spread--rest-operators)
   - [Spread](#spread)
   - [Rest](#rest)
   - [Destructing](#destructing)
      - [Array Destructing](#array-destructing)
      - [Object Destructing](#object-destructing)
1. [Reference and Primitive Types Refresher](#reference-and-primitive-types-refresher)
1. [Refreshing Array Functions](#refreshing-array-functions)
1. [Refreshing JS Keywords](#refreshing-js-keywords)
1. [Build Workflow](#build-workflow)
1. [React Commands](#react-commands)
1. [React Common Features](#react-common-features)
   - [JSX](#jsx)
   - [props](#props-properties)
   - [state & useState()](#state--usestate)
      - [State in Functional-Based Components](#state-in-functional-based-components)
   - [React Hooks](#react-hooks)
   - [Stateful & Stateless Components](#stateful--stateless-components)
   - [Passing Method References & Parameters Between Components](#passing-method-references--parameters-between-components)
   - [Two Way Bonding](#two-way-bonding)
   - [Styling](#styling)
   - [Conditionals](#conditionals)
   - [Lists & Keys](#lists--keys)
   - [Dynamic Styles & Classes](#dynamic-styles--classes)
      - [Radium](#radium-npm-package)
      - [Styled-Components](#styled-components-npm-package)
      - [Styled-Components & Dynamic Styles](#styled-components-npm-package--dynamic-styles)
      - [CSS Modules](#css-modules)
   - [Error Boundaries](#error-boundaries)
   - [Components-Lifecycle](#components-lifecycle)
      - [Class-Based](#class-based)
         - [Creation](#creation)
         - [Update](#update)
      - [Function-Based](#function-based)
         - [useEffect()](#useeffect)
   - [Optimization](#optimization)
      - [shouldComponentUpdate()](#shouldcomponentupdate)
      - [React.memo()](#reactmemo)
      - [PureComponent](#purecomponent)
   - [React Dom Update Approach](#react-dom-update-approach)
   - [Render Adjacent (siblings) elements](#render-adjacent-siblings-elements)
   - [High Order Components (HOC)](#high-order-components-hoc)
   - [Setting State Correctly](#setting-state-correctly)
   - [PropTypes](#proptypes)
   - [Refs](#refs)
      - [Refs in Class-Based Components](#refs-in-class-based-components)
      - [Refs in Function-Based Components](#refs-in-functions-based-components)
   - [React Context API](#react-context-api)
      - [Context API in Class-Based Components](#context-api-in-class-based-components)
      - [Context API in Function-Based Components](#context-api-in-function-based-components)
   - [Events](#events)

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

Класс — шаблон для объекта.

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

## Class Example ES6 / ES7

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

# Refreshing JS Keywords

`static` - в классе обозначает, что доступ к свойству или методу может быть осуществлен без создания экземпляра класса.

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

## State & useState

`state` - используется для изменения компонента внутри себя. Доступен только в компонентах основанных на классах
(class-based components).

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
рамках одного компонента. `state` Не получает данные из вне (от родительских компонентов).
> `this.setState` В компонентах основанных на классах, при изменении
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

### State in Functional-Based Components

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

> `setPersonsState` Не будет совмещать старый и новый объект, а просто перезапишет его
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

## Passing Method References & Parameters Between Components

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

Есть два способа добавления стилей для компонентов:

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
    <div>
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
    </div>
);
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
    <div>
        <button
            style={style}
            onClick={toggleView()}>
            Switch Name
        </button>
        {
            elements
        }
    </div>
);
```

## Lists & Keys

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

Атрибут `key` должен обязательно должен присутствовать и быть уникальным, например `id` или как в этом случае - `index`

## Dynamic Styles & Classes

Стили можно задавать объектом и далее, изменяя этот объект согласно условиям — управлять стилями.

```jsx
const style = {
    backgroundColor: 'green',
    color: 'white',
    font: 'inherit',
    fontWeight: '600',
    border: '1px solid blue',
    padding: '8px',
    cursor: 'pointer'
}

if (personsState.showPersons) {
    style.backgroundColor = 'red';
}

<button style={style}>
    Show persons
</button>
```

Динамически назначать классы можно следующим образом:

1. В зависимости от условия

```jsx
<p className={personsState.showPersons ? 'red' : 'bold'}>And It's working</p>
```

2. С помощью массива строк, содержащих имена классов

```jsx
let classes = ['red', 'bold'].join(' ');

<p className={classes}>And It's working</p>
```

### Radium `npm package`

Пакет, позволяющий использовать медиа запросы, ключевые кадры для анимаций в коде `jsx`. Для использования необходимо
установить пакет с помощью `npm`.

Примеры:

1. Использование для применения псевдоклассов

```jsx
const style = {
    ':hover': {
        backgroundColor: 'lightgreen',
        color: 'black'
    }
}

// При перезаписи необходимо использовать следующий синтаксис
style[':hover'] = {
    backgroundColor: 'salmon',
    color: 'black'
}
```

Также `все` компоненты, где используются псевдоклассы **должны** быть обернуты в `Radium`

```jsx
export default Radium(app);
```

2. Использования для применения медиа запросов

```jsx
const style = {
    '@media (min-width: 500px)': {
        width: '450px'
    }
}
```

При использовании медиа запросов, необходимо обернуть всё содержимое `return` в файле `App.js` в
элемент `<StyleRoot></StyleRoot>`

```jsx
<StyleRoot>
    <div className="App">
    </div>
</StyleRoot>
```

### Styled-Components `npm package`

Позволяет добавлять стили для компонентов, создавая дополнительные компоненты.

```jsx
const StyledDiv = styled.div`
  width: 60%;
  margin: 16px auto;
  border: 1px solid #eee;
  box-shadow: 0 2px 3px #ccc;
  padding: 16px;
  text-align: center;
  @media (min-width: 500px) {
    width: 450px
  }
`;

const person = (props) => {
    return (
        <StyledDiv>
            <p onClick={props.click}>I'm a {props.name} and I am {props.age} years old.</p>
            <p>{props.children}</p>
            <input type='text' onChange={props.changed} value={props.name}/>
        </StyledDiv>
    );
}
```

Внутри компонента создается еще один компонент с именем `StyledDiv` в котором вызывается метод
`styled`.`имя элемента` И с помощью шаблона строк заполняется стилями. Далее используется как элемент (компонент)
в `jsx` коде.

В последствии CSS код подставляется в тэг `<style>` внутри `<head>` со сгенерированным CSS классом, который указывается
в компоненте после сборки

### Styled-Components `npm package` & Dynamic Styles

Для динамического изменения стилей необходимо указывать условие в виде собственного (или обычного)
атрибута в компоненте.

```jsx
<StyledButton
    alt={personsState.showPersons}
    onClick={showPersonsHandler}>
    Show persons
</StyledButton>
```

В последствии, в компоненте динамических стилей, с помощью тернарного оператора и значения условия — переназначать
стили (без обратных слэшей, какое-то экранирование от `MD`).

```jsx
const StyledButton = styled.button`
  background-color: ${props => props.alt ? 'red' : 'green'};
  color: white;
  font: inherit;
  font-weight: 600;
  border: 1px solid blue;
  padding: 8px;
  cursor: pointer;
    &:hover {
      background-color: ${props => props.alt ? 'salmon' : 'lightgreen'};
      color: ${props => props.alt ? 'white' : 'black'};
    }
`;
```

### CSS Modules

> **При использовании `react-scripts` версии > 2.x можно просто именовать CSS файлы следующим
> образом: `App.module.css` и по умолчанию будет использоваться модульный CSS.** Далее файл
> можно использовать с помощью `import classes from './App.module.css';`

Еще одним подходом к реализации стилей в React является `CSS Modules`. Данный вариант позволяет использовать
импортировать стили из `.css` файла как объект. Для этого необходимо в конфигурации (предварительно
выполнив `npm run eject` для получения доступа к файлам конфигурации) изменить следующие параметры:

В файле `config/webpack.config.prod.js` и `config/webpack.config.dev.js` рядом с
`test: /\.css$/` добавить строки в `use:`

```js
use: [
    {
        loader: require.resolve('css-loader'),
        options: {
            importLoaders: 1,
            modules: true, //нужно добавить
            localIdentName: '[name]__[local]__[hash: base64:5]', //нужно добавить
            minimize: true,
            sourceMap: shouldUseSourceMap,
        },
    }
]
```

После данных операций можно будет импортировать стили из файла как объект и использовать свойства этого объекта, пример:

App.css

```css
.red {
    color: red;
}

.bold {
    font-weight: bold;
}
```

App.js

```jsx
import classes from './App.css';

let assignedClasses = [classes.red, classes.bold].join(' ');

return (
    <div>
        <p className={assignedClasses}>It's working</p>
    </div>
);
```

## Error Boundaries

Error Boundary (предохранитель) - позволяет управлять поведением приложения при ошибках. Предохранитель является
компонентом, который оборачивает другие компоненты, в которых может произойти ошибка, например при обращении к серверу.
Хорошей практикой является использовать предохранитель только там, где это действительно необходимо.

ErrorBoundary.js

```jsx
class ErrorBoundary extends React.Component {
    state = {hasError: false};

    componentDidCatch(error, errorInfo) {
        // You can also log the error to an error reporting service
        logErrorToMyService(error, errorInfo);
    }

    render() {
        if (this.state.hasError) {
            // You can render any custom fallback UI
            return <h1>Something went wrong.</h1>;
        }

        return this.props.children;
    }
}
```

**Важно!** Текст, указанный в методе `render()` будет отображаться только после сборки приложения. В режиме разработки
будет выводиться stack trace.

App.js

```jsx
if (personsState.showPersons) {
    persons = (
        <div>
            {personsState.persons.map((person) => {
                return (
                    <ErrorBoundary key={person.id}>
                        <Person
                            name={person.name}
                            age={person.age}
                            changed={event => nameChangedHandler(event, person.id)}
                            click={() => deletePersonHandler(person.id)}>
                            My hobby: Nothing
                        </Person>
                    </ErrorBoundary>
                );
            })}
        </div>
    );
    btnClass = classes.Red;
}
```

Ознакомиться с предохранителями более подробно можно [здесь](https://ru.reactjs.org/docs/error-boundaries.html).

## Components Lifecycle

### Class-based

> **Относится только к компонентам основанных на классах - `class-based components`**

#### Creation

Создание компонента включает в себя следующие, последовательно выполняемые функции:

1. `constructor(props)`

   Нужно вызывать метод `super()` в конструкторе, чтобы запускать свои методы. Обычно используется для
   инициализации `state`. В этом методе не нужно выполнять `http`
   запросы и прочие методы которые выполняются с задержкой или прерывают выполнения кода.

1. `getDerivedStateFromProps(props, state)`

   Когда меняются `props`, есть возможность синхронизировать из с текущим `state`. В этом методе не нужно
   выполнять `http`запросы и прочие методы которые выполняются с задержкой или прерывают выполнения кода.

1. `render()`

   Отображает `jsx` код. В этом методе не нужно выполнять `http` запросы и прочие методы которые выполняются с задержкой
   или прерывают выполнения кода.

1. Render Child Component

   Все включенные в `render()` компоненты будут отображены.

1. `componentDidMount()`

   Основной метод для отправки `http` запросов. В этом методе не следует обновлять `state`

#### Update

Обновление компонента включает в себя следующие, последовательно выполняемые функции:

1. `getDerivedStateFromProps(props, state)`

   Когда меняются `props`, есть возможность синхронизировать из с текущим `state`. В этом методе не нужно
   выполнять `http`запросы и прочие методы которые выполняются с задержкой или прерывают выполнения кода.

1. `shouldComponentUpdate(nextProps, nextState)`

   Позволяет управлять обновлением компонентов. Обычно используется для оптимизации. Сравнивая предыдущий `state` и
   новый `state` можно вернуть `true` если есть различия и требуется обновление, либо вернуть `false` есть различий
   между старым и новым `state` — нет и обновление не требуется.

1. `render()`

   Отображает `jsx` код. В этом методе не нужно выполнять `http` запросы и прочие методы которые выполняются с задержкой
   или прерывают выполнения кода.

1. Update Child Component Props

   Все `props` включенных в `render()` компонентов будут обновлены.

1. `getSnapshotBeforeUpdate(prevProps, prevState)`

   Возвращает снимок (предыдущее состояние) `props`. Например: можно использовать для запоминания места прокрутки
   страницы пользователя, чтобы после обновления компонента была возможность вернуть его туда.

1. `componentDiDUpdate()`

   Метод говорит о том, что `render()` выполнился и можно выполнять `http` запросы и производить прочие блокирующие
   операции.

   **Не стоит обновлять `state` в данном методе, так как компонент будет отрисовываться повторно.**

   **Необходимо следить за обновлением**, так как можно войти в бесконечный цикл — выполняется `http` запрос, по
   получению ответа сервера компонент обновляется, что в свою очередь опять выполняет метод `componentDiDUpdate()`.

1. `componentWillUnmount()`

   Выполнит код перед удалением компонента из видимости.

### Function-based

> **Относится только к компонентам основанных на функциях - `function-based components`
> Иными словами это `React Hooks`**

#### useEffect

По сути объединяет функционал всех `lifecycle-hooks` описанных выше для компонентов основанных на
классах `class-based components`. Внутри метода можно делать `http` запросы и прочие блокирующие операции. Можно
использовать несколько `useEffect` для свойств `props`, которые необходимо регулярно обновлять. Вторым параметром
принимается массив свойств, при обновлении которых нужно обновлять компонент. При указании пустого массива `[]`, код
в `useEffect` выполниться один раз.

```jsx
useEffect(() => {
    console.log('[Cockpit.js] useEffect');
    setTimeout(() => {
        alert('Saved Data to Cloud');
    }, 1000);
}, [props.persons]);
```

Для выполнения кода перед удалением компонента необходимо использовать `return`

```jsx
useEffect(() => {
    console.log('[Cockpit.js] useEffect');

    const timer = setTimeout(() => {
        alert('Saved Data to Cloud');
    }, 1000);

    return () => {
        console.log('[Cockpit.js] useEffect clean up...');
        clearTimeout(timer);
    };
}, []);
```

## Optimization

Если есть уверенность, что при обновлении родительского компонента обновляется и дочерний, то использовать нижеуказанные
методы оптимизации **не нужно**, так как это увеличит нагрузку на приложение из-за того что будут запускаться
бессмысленные проверки изменений.

Оптимизировать нужно только в том случае, если есть понимание, что компонент может **обновляться просто так, не имея на
это причин**.

### shouldComponentUpdate

Функция для оптимизации обновления компонентов основанных на классах. Реализуется с помощью указания метода и внутренней
логики в теле класса. В данном примере компонент будет обновляться только в том случае, если новый состав
свойства `persons` не равен действующему составу.

```jsx
shouldComponentUpdate(nextProps, nextState)
{
    console.log('[Persons.js] shouldComponentUpdate');
    if (nextProps.persons !== this.props.persons) {
        return true;
    } else {
        return false;
    }
}
```

### React.memo

Средство оптимизации обновления компонентов основанных на функциях. Используется для отключения перерисовки компонентов,
данные в которых не обновляются. Для использования необходимо обернуть компонент при экспорте.

```jsx
export default React.memo(component);
```

### PureComponent

PureComponent — это компонент, который имеет встроенный метод `shouldComponentUpdate`. Встроенный метод будет сравнивать
все свойства `state` и решать, обновлять компонент или нет. Если хоть одно из свойств изменилось — компонент будет
обновлён.

```jsx
import React, {PureComponent} from "react";

class Persons extends PureComponent {
}
```

## React DOM Update Approach

Обновление документа происходит следующим образом:

1. При наличии `shouldComponentUpdate()` или `React.memo()` проверяется нужно ли обновлять компонент
1. Вызывается метод `render()` (если проверка в пункте 1 была пройдена)
1. Сравнивается старый **виртуальный** документ и новый **виртуальный** документ (с последними изменениями)
1. Если есть различия — обновляется **реальный** документ.

## Render Adjacent (siblings) Elements

Для вывода нескольких элементов в теле `return()` можно использовать 2 способа:

1. Указать массив как возвращаемое значение, определив свойство `key` для каждого элемента

```jsx
return [
    <p key={"1"} onClick={this.props.clicked}>I'm a {this.props.name} and I am {this.props.age} years old.</p>,
    <p key={"2"}>{this.props.children}</p>,
    <input key={"3"} type='text' onChange={this.props.changed} value={this.props.name}/>
];
```

2. Создать high order component, который будет оборачивать компонент, где необходимо вернуть несколько элементов

Auxiliary.js

```jsx
import React, {Component} from "react";

const aux = props => props.children;

export default aux;
```

Person.js

```jsx
return (
    <Aux>
        <p onClick={this.props.clicked}>I'm a {this.props.name} and I am {this.props.age} years old.</p>
        <p>{this.props.children}</p>
        <input type='text' onChange={this.props.changed} value={this.props.name}/>
    </Aux>
);
```

3. Использовать встроенный элемент - `Fragment` (осуществляет те же самые действия, что и в пункте 2)

```jsx
import React, {Component, Fragment} from "react";

return (
    <Fragment>
        <p onClick={this.props.clicked}>I'm a {this.props.name} and I am {this.props.age} years old.</p>
        <p>{this.props.children}</p>
        <input type='text' onChange={this.props.changed} value={this.props.name}/>
    </Fragment>
);
```

## High Order Components (HOC)

Главным назначением таких компонентов является дополнение дочерних компонентов: их стилизация, логика и так далее. В
основном, компоненты высокого назначения используются для оборачивания дочерних компонентов. Например, для указания
классов.

1. Способ оборачивания через функциональный компонент

WithClass.js

```jsx
import React from "react";

const withClass = props => (
    <div className={props.classes}>
        {props.children}
    </div>
);

export default withClass;
```

App.js

```jsx
return (
    <WithClass classes={classes.App}>
        <button onClick={this.showCockpitHandler}>Toggle Cockpit show</button>
        {this.state.showCockpit ?
            <Cockpit
                title={this.props.appTitle}
                showPersons={this.state.showPersons}
                personsLength={this.state.persons.length}
                clicked={this.showPersonsHandler}
            />
            : null}

        {persons}
    </WithClass>
);
```

2. Способ оборачивания через возвращение функционального компонента и прокидыванием свойств

withClass.js

```jsx
import React from "react";

const withClassNew = (WrappedComponent, className) => {
    return props => (
        <div className={className}>
            <WrappedComponent {...props}/>
        </div>
    );
}

export default withClassNew;
```

Person.js

```jsx
export default withClass(Person, classes.Person);
```

Код указанный выше, вернет новый функциональный компонент, обработанный функцией
`withClassNew()`. С помощью указания `{...props}` мы прокидываем в новый компонент все свойства. Это `{...props}`
превращается (в зависимости от прокинутых свойств) примерно в это `<WrappedComponent name="Ilya" age="23"/>`

> **Первый способ** больше подходит для случаев, когда нужно просто указать стили.
>
> **Второй способ** больше подходит для случаев, когда есть какая-то дополнительная логика для реализации
> в компоненте "оборачивателе", например сбор статистики или аналитики или указание ошибок.

## Setting State Correctly

Состояние (`state`) не меняется перманентно. Состояние может **меняться с задержкой**, так работает React.

В связи с этим не следует использовать следующую конструкцию.

```jsx
this.setState({
    changeCounter: this.state.changeCounter + 1
});
```

Обращаясь к `state` в `this.setState()` нет гарантий, что в текущем `state` свойство changeCounter имеет актуальное
значение, так как может получиться так, что в другом методе значения свойства было изменено, но изменения не успели
примениться к `state`.

Во избежание некорректного поведения, описанного выше, необходимо использовать альтернативный подход

```jsx
this.setState((prevState, props) => {
    return {
        persons: persons,
        showPersons: true,
        changeCounter: prevState.changeCounter + 1
    }
});
```

Таким образом, когда необходимо обновлять значения свойств, основываясь на предыдущих значениях, необходимо использовать
вышеуказанный подход.

## PropTypes

Дополнительная библиотека от разработчиков React, которая позволяет указывать типы для `props`. Полезный инструмент при
работе в команде. Используется как в компонентах основанных на классах, так и в компонентах основанных на функциях.

Типы описываются в файле компонента перед экспортом.

```jsx
Person.propTypes = {
    click: PropTypes.func,
    changed: PropTypes.func,
    name: PropTypes.string,
    age: PropTypes.number
};

export default withClass(Person, classes.Person);
```

## Refs

Специальное свойство для управления любым JSX (HTML) элементом.

### Refs in Class-Based Components

```jsx
componentDidMount()
{
    this.inputElement.focus();
}

<input
    ref={(inputElem) => {
        this.inputElement = inputElem
    }}
    type='text'
    onChange={this.props.changed}
    value={this.props.name}
/>
```

Альтернативный способ создания ссылки

```jsx
constructor()
{
    this.inputElementRef = React.createRef();
}

componentDidMount()
{
    this.inputElementRef.current.focus();
}

<input
    ref={this.inputElementRef}
    type='text'
    onChange={this.props.changed}
    value={this.props.name}
/>
```

### Refs in Functions-Based Components

В теле компонента необходимо инициализировать переменную, которая будет хранить ссылку:

```jsx
const toggleButtonRef = useRef(null);
```

Далее необходимо указать в коде элемента созданную ссылку

```jsx
<button
    ref={toggleButtonRef}
    className={btnClass}
    onClick={props.clicked}>
    Show persons
</button>
```

Затем использовать в функции, **которая исполняется после возвращения `JSX` кода из компонента.** Например `useEffect()`

```jsx
useEffect(() => {
    toggleButtonRef.current.click();

    return () => {
        console.log('[Cockpit.js] useEffect clean up...');
    };
}, []);
```

## React Context API

Технология позволяющая использовать состояние в компонентах, минуя прокидывание через `props`. Например, нам необходимо
использовать данные аутентификации в некоторых компонентах, которые находятся в глубине иерархии (дочерние-дочерних), но
в таком случае, чтобы передать информацию от одного компонента к другому придется передавать значение с помощью `props`
через всю иерархию. `Context` Позволяет избежать этого.

Простыми словами, `Context` это объект (либо другой тип: массив, строка, число), который доступен глобально или где ему
указано быть доступным.

### Context API in Class-Based Components

auth-context.js

```jsx
import React from "react";

const authContext = React.createContext({
    authenticated: false,
    login: () => {
    }
});

export default authContext;
```

Свойства по умолчанию определяются для удобства работы в IDE (авто подстановка).

Для использования необходимо обозначить `Provider` и `Consumer`.

- `Provider` - компонент стоящий выше по иерархии, свойства которого нужно передать компоненту ниже по иерархии
- `Consumer` - компонент, в который необходимо передать данные

App.js

```jsx
<AuthContext.Provider
    value={{authenticated: this.state.authenticated, login: this.loginHandler}}
>
    {this.state.showCockpit ?
        <Cockpit
            title={this.props.appTitle}
            showPersons={this.state.showPersons}
            personsLength={this.state.persons.length}
            clicked={this.showPersonsHandler}
        />
        : null}

    {persons}
</AuthContext.Provider>
```

Person.js

```jsx
<AuthContext.Consumer>
    {context => context.authenticated ? <p>Authenticated</p> : <p>NOT Authenticated</p>}
</AuthContext.Consumer>
```

Переданный в `Provider` в атрибут `value` объект доступен через `context`.
> В данном примере доступ к `context` будет только в рамках рендера `<AuthContext.Consumer>`

Альтернативный способ использования `context`, который позволяет использовать его в методах класса.

Person.js

```jsx
class Person extends Component {
    static contextType = AuthContext;
}
```

Свойство `contextType` позволяет React автоматически получить доступ к `context` и наполнить его значениями.

**Использовать необходимо свойство с именем `context`**

```jsx
{
    this.context.authenticated ?
        <p>Authenticated</p> :
        <p>NOT Authenticated</p>
}
```

### Context API in Function-Based Components

Для использования `context` в компонентах основанных на функциях, необходимо использовать хук `useContext()`

Cockpit.js

```jsx
import AuthContext from "../../context/auth-context";

const cockpit = (props) => {
    const authContext = useContext(AuthContext);

    return (
        <div>
            <button onClick={authContext.login}>Log in</button>
        </div>
    );
}
```

## Events

Основной список событий и примеров доступен в [**документации по событиям**](https://reactjs.org/docs/events.html).
