# 📘 Полное руководство по TypeScript

## Оглавление
1. [Введение в TypeScript](#1-введение-в-typescript)
2. [Основные типы](#2-основные-типы)
3. [Интерфейсы и типы](#3-интерфейсы-и-типы)
4. [Классы и ООП](#4-классы-и-ооп)
5. [Обобщения (Generics)](#5-обобщения-generics)
6. [Декораторы](#6-декораторы)
7. [Модули и пространства имен](#7-модули-и-пространства-имен)
8. [Утилитарные типы](#8-утилитарные-типы)
9. [Продвинутые возможности](#9-продвинутые-возможности)
10. [Практические примеры](#10-практические-примеры)

---

## 1. Введение в TypeScript

### 1.1. Что такое TypeScript?

TypeScript — это строго типизированное надмножество JavaScript, которое компилируется в чистый JavaScript. Он добавляет статическую типизацию, интерфейсы, обобщения и другие возможности для масштабируемой разработки.

### 1.2. Установка и настройка

```bash
# Глобальная установка
npm install -g typescript

# Локальная установка в проект
npm install --save-dev typescript

# Инициализация конфигурации
tsc --init
```

### 1.3. Базовый пример

```typescript
// Объявление переменной с типом
let message: string = "Hello, TypeScript!";
let count: number = 42;
let isActive: boolean = true;

// Функция с типами параметров и возвращаемого значения
function greet(name: string): string {
    return `Привет, ${name}!`;
}

// Вызов функции
console.log(greet("Иван")); // Привет, Иван!
```

---

## 2. Основные типы

### 2.1. Примитивные типы

```typescript
// String - строки
let username: string = "Алексей";
let email: string = `user@example.com`;

// Number - числа (целые, дробные, hex, binary, octal)
let age: number = 25;
let price: number = 99.99;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;

// Boolean - логические значения
let isLoggedIn: boolean = true;
let hasPermission: boolean = false;

// Null и Undefined
let emptyValue: null = null;
let notDefined: undefined = undefined;

// Symbol - уникальные идентификаторы
let uniqueId: symbol = Symbol("id");

// BigInt - большие целые числа
let largeNumber: bigint = 9007199254740991n;
```

### 2.2. Массивы и кортежи

```typescript
// Массивы
let numbers: number[] = [1, 2, 3, 4, 5];
let strings: Array<string> = ["a", "b", "c"];
let mixed: (string | number)[] = ["hello", 42, "world"];

// Readonly массивы
let readonlyNumbers: readonly number[] = [1, 2, 3];
// readonlyNumbers.push(4); // Ошибка!

// Кортежи (Tuples) - массивы с фиксированной длиной и типами
let user: [string, number, boolean] = ["Иван", 25, true];
let [name, userAge, isStudent] = user;

// Опциональные элементы кортежа
let optionalTuple: [string, number?] = ["hello"];
let tupleWithRest: [string, ...number[]] = ["hello", 1, 2, 3];
```

### 2.3. Enum (перечисления)

```typescript
// Числовые enum
enum UserRole {
    Admin,      // 0
    Editor,     // 1
    Viewer,     // 2
    Guest       // 3
}

// Строковые enum
enum HttpStatus {
    OK = "200",
    NotFound = "404",
    InternalError = "500"
}

// Enum с вычисляемыми значениями
enum FileSize {
    KB = 1024,
    MB = KB * 1024,
    GB = MB * 1024
}

// Использование
let role: UserRole = UserRole.Admin;
console.log(role); // 0
console.log(UserRole[0]); // "Admin"

// Const enum (оптимизированный)
const enum Direction {
    Up = "UP",
    Down = "DOWN",
    Left = "LEFT",
    Right = "RIGHT"
}
```

### 2.4. Any, Unknown, Never, Void

```typescript
// Any - отключает проверку типов (используйте осторожно!)
let dynamicData: any = "string";
dynamicData = 42;
dynamicData = true;

// Unknown - типобезопасная альтернатива any
let userInput: unknown = "hello";

// Проверка типа перед использованием
if (typeof userInput === "string") {
    console.log(userInput.toUpperCase());
}

// Void - отсутствие возвращаемого значения
function logMessage(message: string): void {
    console.log(message);
    // return; // Можно вернуть undefined
}

// Never - функция никогда не завершается
function throwError(message: string): never {
    throw new Error(message);
}

function infiniteLoop(): never {
    while (true) {
        // Бесконечный цикл
    }
}
```

### 2.5. Union и Intersection типы

```typescript
// Union Types (объединение)
type ID = string | number;
let userId: ID = "user123";
userId = 456;

type Status = "loading" | "success" | "error";
let requestStatus: Status = "loading";

// Intersection Types (пересечение)
interface Person {
    name: string;
    age: number;
}

interface Employee {
    employeeId: string;
    department: string;
}

type EmployeePerson = Person & Employee;

const worker: EmployeePerson = {
    name: "Анна",
    age: 30,
    employeeId: "EMP001",
    department: "IT"
};

// Сужение типов (Type Narrowing)
function processValue(value: string | number) {
    if (typeof value === "string") {
        return value.toUpperCase();
    }
    return value.toFixed(2);
}
```

### 2.6. Литеральные типы

```typescript
// Строковые литералы
type Color = "red" | "green" | "blue";
let myColor: Color = "red";

// Числовые литералы
type DiceValue = 1 | 2 | 3 | 4 | 5 | 6;
let roll: DiceValue = 4;

// Логические литералы
type TrueOrFalse = true | false;

// Шаблонные литералы (Template Literal Types)
type HTTPMethod = `http://${string}`;
type EventName = `on${Capitalize<string>}`;

type Greeting = `Hello ${string}`;
let hello: Greeting = "Hello World";
```

---

## 3. Интерфейсы и типы

### 3.1. Интерфейсы (Interfaces)

```typescript
// Базовый интерфейс
interface User {
    id: number;
    name: string;
    email: string;
    age?: number; // Опциональное свойство
    readonly createdAt: Date; // Только для чтения
}

// Использование интерфейса
const user: User = {
    id: 1,
    name: "Иван",
    email: "ivan@example.com",
    createdAt: new Date()
};

// Наследование интерфейсов
interface Admin extends User {
    permissions: string[];
    role: "admin" | "superadmin";
}

// Интерфейс с методами
interface Greetable {
    name: string;
    greet(): string;
    greetWithMessage(message: string): void;
}

// Реализация интерфейса классом
class Person implements Greetable {
    constructor(public name: string) {}
    
    greet(): string {
        return `Hello, I'm ${this.name}`;
    }
    
    greetWithMessage(message: string): void {
        console.log(`${message}, ${this.name}`);
    }
}

// Индексные сигнатуры
interface Dictionary {
    [key: string]: string | number;
}

const dict: Dictionary = {
    name: "John",
    age: 30
};

// Callback интерфейс
interface SearchFunction {
    (source: string, subString: string): boolean;
}

const mySearch: SearchFunction = (source, subString) => {
    return source.includes(subString);
};
```

### 3.2. Type Aliases (псевдонимы типов)

```typescript
// Базовый type alias
type Point = {
    x: number;
    y: number;
};

type ID = string | number;

// Union types
type Status = "pending" | "approved" | "rejected";

// Tuple types
type Coordinate = [number, number];

// Function types
type Callback = (data: any) => void;
type MathOperation = (a: number, b: number) => number;

// Mapped types
type ReadonlyPoint = {
    readonly [P in keyof Point]: Point[P];
};

// Conditional types
type IsString<T> = T extends string ? true : false;
type Result = IsString<"hello">; // true
type Result2 = IsString<number>; // false
```

### 3.3. Интерфейс vs Type

```typescript
// Когда использовать интерфейс:
// 1. Для определения структуры объектов
// 2. Для наследования
// 3. Для реализации классов

interface Animal {
    name: string;
    makeSound(): void;
}

interface Dog extends Animal {
    breed: string;
}

// Когда использовать type:
// 1. Для union типов
// 2. Для кортежей
// 3. Для сложных типов

type ID = string | number;
type Response = [string, number];
type Callback = (error: Error | null, data: any) => void;

// Type может быть переопределен (через &)
type User = {
    name: string;
};

type UserWithAge = User & {
    age: number;
};

// Интерфейс можно расширять (declaration merging)
interface Box {
    width: number;
}

interface Box {
    height: number; // Объединение
}

const box: Box = { width: 10, height: 20 };
```

---

## 4. Классы и ООП

### 4.1. Классы в TypeScript

```typescript
// Базовый класс
class Animal {
    // Свойства класса
    public name: string;
    private age: number;
    protected species: string;
    readonly id: number;
    
    // Статическое свойство
    static kingdom: string = "Animalia";
    
    // Конструктор
    constructor(name: string, age: number, species: string) {
        this.name = name;
        this.age = age;
        this.species = species;
        this.id = Math.random();
    }
    
    // Метод
    public makeSound(): void {
        console.log(`${this.name} издает звук`);
    }
    
    // Приватный метод
    private getAge(): number {
        return this.age;
    }
    
    // Защищенный метод
    protected getSpecies(): string {
        return this.species;
    }
    
    // Статический метод
    static getKingdom(): string {
        return Animal.kingdom;
    }
}

// Наследование
class Dog extends Animal {
    private breed: string;
    
    constructor(name: string, age: number, breed: string) {
        super(name, age, "Canis familiaris");
        this.breed = breed;
    }
    
    // Переопределение метода
    makeSound(): void {
        console.log(`${this.name} гавкает!`);
    }
    
    // Дополнительный метод
    wagTail(): void {
        console.log("Виляет хвостом");
    }
    
    // Доступ к защищенному свойству родителя
    showSpecies(): void {
        console.log(`Вид: ${this.species}`);
    }
}
```

### 4.2. Модификаторы доступа

```typescript
class AccessExample {
    // public - доступно везде (по умолчанию)
    public publicField: string = "public";
    
    // private - доступно только внутри класса
    private privateField: string = "private";
    
    // protected - доступно внутри класса и наследников
    protected protectedField: string = "protected";
    
    // readonly - только для чтения
    readonly readonlyField: string = "readonly";
    
    // static - принадлежит классу, а не экземпляру
    static staticField: string = "static";
    
    // Параметры конструктора с модификаторами
    constructor(
        public name: string,
        private age: number,
        protected id: string
    ) {}
    
    getAge(): number {
        return this.age; // доступно
    }
}

class SubClass extends AccessExample {
    test() {
        this.publicField; // доступно
        this.protectedField; // доступно
        // this.privateField; // Ошибка!
        this.id; // доступно (protected)
    }
}
```

### 4.3. Абстрактные классы

```typescript
// Абстрактный класс
abstract class Shape {
    constructor(public color: string) {}
    
    // Абстрактный метод (должен быть реализован в наследнике)
    abstract getArea(): number;
    
    // Конкретный метод
    getColor(): string {
        return this.color;
    }
}

// Реализация абстрактного класса
class Circle extends Shape {
    constructor(color: string, private radius: number) {
        super(color);
    }
    
    getArea(): number {
        return Math.PI * this.radius ** 2;
    }
}

class Rectangle extends Shape {
    constructor(color: string, private width: number, private height: number) {
        super(color);
    }
    
    getArea(): number {
        return this.width * this.height;
    }
}

// Использование
const circle: Shape = new Circle("red", 5);
console.log(circle.getArea()); // 78.54
console.log(circle.getColor()); // red
```

### 4.4. Getter и Setter

```typescript
class Temperature {
    private _celsius: number = 0;
    
    // Getter
    get celsius(): number {
        return this._celsius;
    }
    
    // Setter с валидацией
    set celsius(value: number) {
        if (value < -273.15) {
            throw new Error("Температура ниже абсолютного нуля");
        }
        this._celsius = value;
    }
    
    // Вычисляемое свойство
    get fahrenheit(): number {
        return (this._celsius * 9/5) + 32;
    }
    
    set fahrenheit(value: number) {
        this.celsius = (value - 32) * 5/9;
    }
}

const temp = new Temperature();
temp.celsius = 25;
console.log(temp.fahrenheit); // 77
temp.fahrenheit = 100;
console.log(temp.celsius); // 37.777...
```

### 4.5. Реализация интерфейсов

```typescript
interface Printable {
    print(): void;
    getContent(): string;
}

interface Serializable {
    serialize(): string;
    deserialize(data: string): void;
}

// Класс может реализовывать несколько интерфейсов
class Document implements Printable, Serializable {
    constructor(private content: string) {}
    
    print(): void {
        console.log(`Печать: ${this.content}`);
    }
    
    getContent(): string {
        return this.content;
    }
    
    serialize(): string {
        return JSON.stringify({ content: this.content });
    }
    
    deserialize(data: string): void {
        const parsed = JSON.parse(data);
        this.content = parsed.content;
    }
}
```

---

## 5. Обобщения (Generics)

### 5.1. Базовое использование

```typescript
// Обобщенная функция
function identity<T>(value: T): T {
    return value;
}

// Использование с указанием типа
let result1 = identity<string>("hello");
let result2 = identity<number>(42);

// Без указания типа (вывод типа)
let result3 = identity("world");

// Несколько обобщенных параметров
function merge<T, U>(obj1: T, obj2: U): T & U {
    return { ...obj1, ...obj2 };
}

const merged = merge({ name: "John" }, { age: 30 });
// merged.name и merged.age доступны

// Ограничения (Constraints)
interface HasLength {
    length: number;
}

function logLength<T extends HasLength>(item: T): T {
    console.log(item.length);
    return item;
}

logLength("hello"); // OK
logLength([1, 2, 3]); // OK
// logLength(42); // Ошибка!
```

### 5.2. Обобщенные интерфейсы

```typescript
// Обобщенный интерфейс
interface Box<T> {
    value: T;
    getValue(): T;
    setValue(value: T): void;
}

// Реализация интерфейса
class NumberBox implements Box<number> {
    constructor(public value: number) {}
    
    getValue(): number {
        return this.value;
    }
    
    setValue(value: number): void {
        this.value = value;
    }
}

// Обобщенный интерфейс для функций
interface Comparator<T> {
    (a: T, b: T): number;
}

const numberComparator: Comparator<number> = (a, b) => a - b;
const stringComparator: Comparator<string> = (a, b) => a.localeCompare(b);
```

### 5.3. Обобщенные классы

```typescript
// Обобщенный класс
class Stack<T> {
    private items: T[] = [];
    
    push(item: T): void {
        this.items.push(item);
    }
    
    pop(): T | undefined {
        return this.items.pop();
    }
    
    peek(): T | undefined {
        return this.items[this.items.length - 1];
    }
    
    isEmpty(): boolean {
        return this.items.length === 0;
    }
    
    size(): number {
        return this.items.length;
    }
}

// Использование
const numberStack = new Stack<number>();
numberStack.push(1);
numberStack.push(2);

const stringStack = new Stack<string>();
stringStack.push("hello");

// Класс с несколькими обобщениями
class Pair<K, V> {
    constructor(public key: K, public value: V) {}
    
    toString(): string {
        return `${this.key}: ${this.value}`;
    }
}

const pair = new Pair<string, number>("age", 30);
```

### 5.4. Утилитарные типы с Generics

```typescript
// Type guards с generics
function isArray<T>(value: unknown): value is T[] {
    return Array.isArray(value);
}

// Mapped types
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

type Nullable<T> = {
    [P in keyof T]: T[P] | null;
};

type Options<T> = {
    [P in keyof T]?: T[P];
};

// Conditional types с generics
type TypeName<T> =
    T extends string ? "string" :
    T extends number ? "number" :
    T extends boolean ? "boolean" :
    T extends undefined ? "undefined" :
    T extends null ? "null" :
    T extends Function ? "function" :
    "object";

type Result1 = TypeName<string>; // "string"
type Result2 = TypeName<number[]>; // "object"
```

### 5.5. Сужение типов в Generics

```typescript
// Использование ключевого слова keyof
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}

const person = {
    name: "Иван",
    age: 30
};

const nameValue = getProperty(person, "name"); // string
const ageValue = getProperty(person, "age"); // number
// getProperty(person, "email"); // Ошибка!

// Класс с динамическими ключами
class ObjectWrapper<T> {
    constructor(private data: T) {}
    
    get<K extends keyof T>(key: K): T[K] {
        return this.data[key];
    }
    
    set<K extends keyof T>(key: K, value: T[K]): void {
        this.data[key] = value;
    }
}

const wrapper = new ObjectWrapper({ id: 1, name: "John" });
const id = wrapper.get("id"); // number
wrapper.set("name", "Jane");
```

---

## 6. Декораторы

### 6.1. Настройка декораторов

```json
// tsconfig.json
{
    "compilerOptions": {
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true
    }
}
```

### 6.2. Классовые декораторы

```typescript
// Базовый декоратор класса
function sealed(constructor: Function) {
    Object.seal(constructor);
    Object.seal(constructor.prototype);
}

// Декоратор с параметрами
function logger<T extends { new(...args: any[]): {} }>(prefix: string) {
    return function(constructor: T) {
        return class extends constructor {
            constructor(...args: any[]) {
                console.log(`${prefix}: Создание экземпляра ${constructor.name}`);
                super(...args);
            }
        };
    };
}

@sealed
@logger("LOG")
class UserService {
    constructor(public name: string) {}
    
    getUser() {
        return this.name;
    }
}
```

### 6.3. Декораторы методов

```typescript
// Декоратор для логирования вызовов
function log(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args: any[]) {
        console.log(`Вызов ${propertyKey} с аргументами:`, args);
        const result = originalMethod.apply(this, args);
        console.log(`Результат ${propertyKey}:`, result);
        return result;
    };
    
    return descriptor;
}

// Декоратор для измерения времени выполнения
function measure(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args: any[]) {
        const start = performance.now();
        const result = originalMethod.apply(this, args);
        const end = performance.now();
        console.log(`${propertyKey} выполнен за ${end - start}ms`);
        return result;
    };
    
    return descriptor;
}

// Декоратор для проверки авторизации
function authorize(role: string) {
    return function(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
        const originalMethod = descriptor.value;
        
        descriptor.value = function(...args: any[]) {
            if (this.userRole !== role) {
                throw new Error(`Доступ запрещен. Требуется роль: ${role}`);
            }
            return originalMethod.apply(this, args);
        };
        
        return descriptor;
    };
}

class ApiService {
    private userRole = "admin";
    
    @log
    @measure
    getUser(id: number) {
        return { id, name: "User" };
    }
    
    @authorize("admin")
    deleteUser(id: number) {
        console.log(`Пользователь ${id} удален`);
    }
}
```

### 6.4. Декораторы свойств

```typescript
// Декоратор для валидации свойств
function validateRange(min: number, max: number) {
    return function(target: any, propertyKey: string) {
        let value: number;
        
        const getter = function() {
            return value;
        };
        
        const setter = function(newValue: number) {
            if (newValue < min || newValue > max) {
                throw new Error(`${propertyKey} должен быть между ${min} и ${max}`);
            }
            value = newValue;
        };
        
        Object.defineProperty(target, propertyKey, {
            get: getter,
            set: setter
        });
    };
}

// Декоратор для преобразования
function uppercase(target: any, propertyKey: string) {
    let value: string;
    
    const getter = function() {
        return value;
    };
    
    const setter = function(newValue: string) {
        value = newValue.toUpperCase();
    };
    
    Object.defineProperty(target, propertyKey, {
        get: getter,
        set: setter
    });
}

class Product {
    @validateRange(0, 100)
    price: number;
    
    @uppercase
    name: string;
    
    constructor(price: number, name: string) {
        this.price = price;
        this.name = name;
    }
}
```

### 6.5. Декораторы параметров

```typescript
// Декоратор для параметров
function required(target: any, propertyKey: string, parameterIndex: number) {
    const existingRequiredParameters: number[] = 
        Reflect.getOwnMetadata("required", target, propertyKey) || [];
    existingRequiredParameters.push(parameterIndex);
    Reflect.defineMetadata("required", existingRequiredParameters, target, propertyKey);
}

// Декоратор для проверки параметров
function validate(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args: any[]) {
        const requiredParams: number[] = 
            Reflect.getOwnMetadata("required", target, propertyKey) || [];
        
        requiredParams.forEach(index => {
            if (args[index] === undefined || args[index] === null) {
                throw new Error(`Параметр ${index} обязателен`);
            }
        });
        
        return originalMethod.apply(this, args);
    };
    
    return descriptor;
}

class UserController {
    @validate
    createUser(
        @required name: string,
        @required email: string,
        age?: number
    ) {
        console.log(`Создан пользователь: ${name}, ${email}`);
    }
}
```

---

## 7. Модули и пространства имен

### 7.1. ES6 Модули

```typescript
// user.ts - экспорт
export interface User {
    id: number;
    name: string;
}

export class UserService {
    private users: User[] = [];
    
    addUser(user: User): void {
        this.users.push(user);
    }
    
    getUsers(): User[] {
        return this.users;
    }
}

export const DEFAULT_USER: User = {
    id: 0,
    name: "Гость"
};

// Экспорт по умолчанию
export default function createUser(name: string): User {
    return { id: Date.now(), name };
}

// app.ts - импорт
import createUser, { User, UserService, DEFAULT_USER } from './user';

const user = createUser("Иван");
const service = new UserService();
service.addUser(user);
```

### 7.2. Пространства имен (Namespaces)

```typescript
// Пространство имен для группировки кода
namespace Validation {
    export interface StringValidator {
        isValid(s: string): boolean;
    }
    
    export class EmailValidator implements StringValidator {
        private emailRegex = /^[^\s@]+@([^\s@]+\.)+[^\s@]+$/;
        
        isValid(s: string): boolean {
            return this.emailRegex.test(s);
        }
    }
    
    export class PhoneValidator implements StringValidator {
        private phoneRegex = /^\+?[0-9]{10,15}$/;
        
        isValid(s: string): boolean {
            return this.phoneRegex.test(s);
        }
    }
}

// Вложенные пространства имен
namespace Utils {
    export namespace StringUtils {
        export function capitalize(str: string): string {
            return str.charAt(0).toUpperCase() + str.slice(1);
        }
        
        export function reverse(str: string): string {
            return str.split('').reverse().join('');
        }
    }
    
    export namespace NumberUtils {
        export function clamp(value: number, min: number, max: number): number {
            return Math.min(Math.max(value, min), max);
        }
    }
}

// Использование
const emailValidator = new Validation.EmailValidator();
console.log(emailValidator.isValid("test@example.com")); // true

const capitalized = Utils.StringUtils.capitalize("hello");
console.log(capitalized); // "Hello"
```

### 7.3. Трехслэшовые ссылки

```typescript
/// <reference path="user.ts" />
/// <reference types="node" />

// Для работы с глобальными типами
declare namespace MyLib {
    function doSomething(): void;
    const version: string;
}
```

---

## 8. Утилитарные типы

### 8.1. Встроенные утилитарные типы

```typescript
interface Todo {
    id: number;
    title: string;
    description: string;
    completed: boolean;
    createdAt: Date;
}

// Partial - все свойства становятся опциональными
type PartialTodo = Partial<Todo>;
// { id?: number; title?: string; ... }

// Required - все свойства обязательные
type RequiredTodo = Required<PartialTodo>;

// Readonly - все свойства только для чтения
type ReadonlyTodo = Readonly<Todo>;

// Pick - выбор определенных свойств
type TodoPreview = Pick<Todo, "id" | "title" | "completed">;

// Omit - исключение определенных свойств
type TodoWithoutDescription = Omit<Todo, "description">;

// Record - создание типа с ключами K и значениями T
type UserMap = Record<string, User>;
const users: UserMap = {
    "user1": { id: 1, name: "John" },
    "user2": { id: 2, name: "Jane" }
};

// Exclude - исключение типов из объединения
type T1 = Exclude<"a" | "b" | "c", "a" | "b">; // "c"

// Extract - извлечение типов из объединения
type T2 = Extract<"a" | "b" | "c", "a" | "d">; // "a"

// NonNullable - исключение null и undefined
type T3 = NonNullable<string | number | null | undefined>; // string | number

// ReturnType - тип возвращаемого значения функции
type Fn = (x: number) => string;
type Result = ReturnType<Fn>; // string

// Parameters - тип параметров функции
type Params = Parameters<(a: string, b: number) => void>; // [string, number]

// ConstructorParameters - тип параметров конструктора
class Person {
    constructor(name: string, age: number) {}
}
type PersonParams = ConstructorParameters<typeof Person>; // [string, number]
```

### 8.2. Создание своих утилитарных типов

```typescript
// DeepReadonly - рекурсивный readonly
type DeepReadonly<T> = {
    readonly [P in keyof T]: T[P] extends object ? DeepReadonly<T[P]> : T[P];
};

// DeepPartial - рекурсивный partial
type DeepPartial<T> = {
    [P in keyof T]?: T[P] extends object ? DeepPartial<T[P]> : T[P];
};

// Nullable - делает все поля nullable
type Nullable<T> = {
    [P in keyof T]: T[P] | null;
};

// ValueOf - тип значений объекта
type ValueOf<T> = T[keyof T];

// AsyncFunction - тип для асинхронной функции
type AsyncFunction<T> = (...args: any[]) => Promise<T>;

// ExtractKeysOfType - извлечение ключей определенного типа
type ExtractKeysOfType<T, U> = {
    [P in keyof T]: T[P] extends U ? P : never;
}[keyof T];

// Пример использования
interface Config {
    name: string;
    age: number;
    address: {
        city: string;
        street: string;
    };
}

type DeepReadonlyConfig = DeepReadonly<Config>;
const config: DeepReadonlyConfig = {
    name: "John",
    age: 30,
    address: {
        city: "Moscow",
        street: "Tverskaya"
    }
};
// config.name = "Jane"; // Ошибка!
// config.address.city = "SPb"; // Ошибка!
```

### 8.3. Условные типы (Conditional Types)

```typescript
// Базовый условный тип
type IsArray<T> = T extends any[] ? true : false;
type A = IsArray<string[]>; // true
type B = IsArray<number>; // false

// Распределительные условные типы
type ToArray<T> = T extends any ? T[] : never;
type StrArrOrNumArr = ToArray<string | number>; // string[] | number[]

// Тип с infer
type ArrayType<T> = T extends (infer U)[] ? U : never;
type Element = ArrayType<string[]>; // string

type ReturnType1<T> = T extends (...args: any[]) => infer R ? R : never;

// Продвинутые условные типы
type DeepNonNullable<T> = {
    [P in keyof T]: T[P] extends object ? DeepNonNullable<T[P]> : NonNullable<T[P]>;
};

type FunctionPropertyNames<T> = {
    [K in keyof T]: T[K] extends Function ? K : never;
}[keyof T];

type NonFunctionPropertyNames<T> = {
    [K in keyof T]: T[K] extends Function ? never : K;
}[keyof T];
```

---

## 9. Продвинутые возможности

### 9.1. Type Guards

```typescript
// Пользовательский type guard
function isString(value: unknown): value is string {
    return typeof value === "string";
}

function isNumber(value: unknown): value is number {
    return typeof value === "number";
}

function isObject(value: unknown): value is Record<string, unknown> {
    return typeof value === "object" && value !== null;
}

// Type guard для классов
class Bird {
    fly() { console.log("Flying"); }
    layEggs() { console.log("Laying eggs"); }
}

class Fish {
    swim() { console.log("Swimming"); }
    layEggs() { console.log("Laying eggs"); }
}

function isBird(animal: Bird | Fish): animal is Bird {
    return (animal as Bird).fly !== undefined;
}

// Использование
function processAnimal(animal: Bird | Fish) {
    if (isBird(animal)) {
        animal.fly(); // TypeScript знает, что это Bird
    } else {
        animal.swim(); // TypeScript знает, что это Fish
    }
}

// Type guard для интерфейсов
interface Car {
    type: "car";
    wheels: number;
    engine: string;
}

interface Bike {
    type: "bike";
    wheels: number;
    hasBell: boolean;
}

function isCar(vehicle: Car | Bike): vehicle is Car {
    return vehicle.type === "car";
}

// Type predicate с generics
function isOfType<T>(value: unknown, property: keyof T): value is T {
    return value !== null && typeof value === "object" && property in value;
}
```

### 9.2. Assertion Functions

```typescript
// Функции утверждения
function assert(condition: any, message?: string): asserts condition {
    if (!condition) {
        throw new Error(message || "Assertion failed");
    }
}

function assertIsString(value: any): asserts value is string {
    if (typeof value !== "string") {
        throw new Error("Value is not a string");
    }
}

function assertIsNumber(value: any): asserts value is number {
    if (typeof value !== "number") {
        throw new Error("Value is not a number");
    }
}

// Использование
function processInput(input: unknown) {
    assertIsString(input);
    // Теперь TypeScript знает, что input - string
    console.log(input.toUpperCase());
}

// Асинхронные утверждения
async function assertAsync(condition: Promise<boolean>): Promise<void> {
    const result = await condition;
    if (!result) {
        throw new Error("Async assertion failed");
    }
}

// Утверждение для объектов
function assertHasProperty<T extends object, K extends string>(
    obj: T,
    prop: K
): asserts obj is T & Record<K, unknown> {
    if (!(prop in obj)) {
        throw new Error(`Object missing property: ${prop}`);
    }
}

const userData: unknown = { name: "John", age: 30 };
assertHasProperty(userData, "name");
console.log(userData.name); // TypeScript знает, что name существует
```

### 9.3. Mapped Types

```typescript
// Базовые mapped types
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

type Mutable<T> = {
    -readonly [P in keyof T]: T[P];
};

type Nullable<T> = {
    [P in keyof T]: T[P] | null;
};

type Optional<T> = {
    [P in keyof T]?: T[P];
};

// Добавление префикса/суффикса к ключам
type AddPrefix<T, P extends string> = {
    [K in keyof T as `${P}${K & string}`]: T[K];
};

type AddSuffix<T, S extends string> = {
    [K in keyof T as `${K & string}${S}`]: T[K];
};

// Фильтрация свойств
type FilterByType<T, U> = {
    [P in keyof T as T[P] extends U ? P : never]: T[P];
};

// Пример
interface User {
    id: number;
    name: string;
    age: number;
    email: string;
}

type StringProperties = FilterByType<User, string>; // { name: string; email: string; }
type NumberProperties = FilterByType<User, number>; // { id: number; age: number; }
type UserWithPrefix = AddPrefix<User, "user_">; // { user_id: number; user_name: string; ... }
```

### 9.4. Template Literal Types

```typescript
// Базовые шаблонные литералы
type Color = "red" | "green" | "blue";
type Size = "small" | "medium" | "large";

type ColorSize = `${Color}-${Size}`;
// "red-small" | "red-medium" | "red-large" | "green-small" | ...

// Манипуляции со строками
type UppercaseGreeting = Uppercase<"hello">; // "HELLO"
type LowercaseGreeting = Lowercase<"WORLD">; // "world"
type CapitalizeWord = Capitalize<"hello world">; // "Hello world"
type UncapitalizeWord = Uncapitalize<"Hello">; // "hello"

// Создание CSS свойств
type CSSUnit = "px" | "em" | "rem" | "%";
type CSSValue = `${number}${CSSUnit}`;

// Создание событий
type EventType = "click" | "hover" | "focus";
type HandlerName = `on${Capitalize<EventType>}`; // "onClick" | "onHover" | "onFocus"

// Продвинутый пример: пути к объектам
type ObjectPaths<T, Prefix extends string = ""> = {
    [K in keyof T]: T[K] extends object
        ? ObjectPaths<T[K], `${Prefix}${K & string}.`>
        : `${Prefix}${K & string}`;
}[keyof T];

interface NestedObject {
    user: {
        name: string;
        address: {
            city: string;
            street: string;
        };
    };
    settings: {
        theme: string;
    };
}

type Paths = ObjectPaths<NestedObject>;
// "user.name" | "user.address.city" | "user.address.street" | "settings.theme"
```

### 9.5. Типизация this

```typescript
// Аннотация this
interface UIElement {
    addClickListener(onclick: (this: void, e: Event) => void): void;
}

class Handler {
    private name: string = "Handler";
    
    // Использование this как параметра
    onClick(this: Handler, e: Event) {
        console.log(this.name);
    }
    
    // Стрелочная функция для сохранения контекста
    onClickArrow = (e: Event) => {
        console.log(this.name);
    };
}

// ThisType для контекста
interface ObjectDescriptor {
    name: string;
    methods: {
        [key: string]: (this: { name: string }) => void;
    };
}

function createObject<T>(desc: ObjectDescriptor & ThisType<T>): T {
    return {} as T;
}

const obj = createObject({
    name: "MyObject",
    methods: {
        greet() {
            console.log(this.name); // this имеет тип { name: string }
        }
    }
});
```

---

## 10. Практические примеры

### 10.1. API клиент с TypeScript

```typescript
// Типы для API
interface ApiResponse<T> {
    data: T;
    status: number;
    message: string;
    timestamp: string;
}

interface User {
    id: number;
    name: string;
    email: string;
    role: "admin" | "user" | "guest";
}

interface Post {
    id: number;
    title: string;
    content: string;
    userId: number;
    createdAt: Date;
}

// API клиент с generics
class ApiClient {
    private baseUrl: string;
    private headers: HeadersInit;
    
    constructor(baseUrl: string, token?: string) {
        this.baseUrl = baseUrl;
        this.headers = {
            "Content-Type": "application/json",
            ...(token && { Authorization: `Bearer ${token}` })
        };
    }
    
    async get<T>(endpoint: string): Promise<ApiResponse<T>> {
        const response = await fetch(`${this.baseUrl}${endpoint}`, {
            method: "GET",
            headers: this.headers
        });
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const data = await response.json();
        return {
            data,
            status: response.status,
            message: "Success",
            timestamp: new Date().toISOString()
        };
    }
    
    async post<T, U>(endpoint: string, body: U): Promise<ApiResponse<T>> {
        const response = await fetch(`${this.baseUrl}${endpoint}`, {
            method: "POST",
            headers: this.headers,
            body: JSON.stringify(body)
        });
        
        return response.json();
    }
    
    async put<T, U>(endpoint: string, body: U): Promise<ApiResponse<T>> {
        const response = await fetch(`${this.baseUrl}${endpoint}`, {
            method: "PUT",
            headers: this.headers,
            body: JSON.stringify(body)
        });
        
        return response.json();
    }
    
    async delete<T>(endpoint: string): Promise<ApiResponse<T>> {
        const response = await fetch(`${this.baseUrl}${endpoint}`, {
            method: "DELETE",
            headers: this.headers
        });
        
        return response.json();
    }
}

// Сервисы с наследованием
class UserService {
    constructor(private apiClient: ApiClient) {}
    
    async getUsers(): Promise<User[]> {
        const response = await this.apiClient.get<User[]>("/users");
        return response.data;
    }
    
    async getUser(id: number): Promise<User> {
        const response = await this.apiClient.get<User>(`/users/${id}`);
        return response.data;
    }
    
    async createUser(user: Omit<User, "id">): Promise<User> {
        const response = await this.apiClient.post<User, Omit<User, "id">>("/users", user);
        return response.data;
    }
    
    async updateUser(id: number, user: Partial<User>): Promise<User> {
        const response = await this.apiClient.put<User, Partial<User>>(`/users/${id}`, user);
        return response.data;
    }
    
    async deleteUser(id: number): Promise<void> {
        await this.apiClient.delete(`/users/${id}`);
    }
}
```

### 10.2. State Management с TypeScript

```typescript
// Типы действий
type Action<T = any> = {
    type: string;
    payload?: T;
};

type Reducer<S, A extends Action> = (state: S, action: A) => S;

// Store с generics
class Store<S, A extends Action> {
    private state: S;
    private reducers: Map<string, Reducer<S, A>> = new Map();
    private listeners: Set<(state: S) => void> = new Set();
    
    constructor(initialState: S) {
        this.state = initialState;
    }
    
    addReducer(type: string, reducer: Reducer<S, A>): void {
        this.reducers.set(type, reducer);
    }
    
    dispatch(action: A): void {
        const reducer = this.reducers.get(action.type);
        if (reducer) {
            const newState = reducer(this.state, action);
            this.state = newState;
            this.notifyListeners();
        }
    }
    
    subscribe(listener: (state: S) => void): () => void {
        this.listeners.add(listener);
        return () => this.listeners.delete(listener);
    }
    
    getState(): S {
        return { ...this.state };
    }
    
    private notifyListeners(): void {
        this.listeners.forEach(listener => listener(this.state));
    }
}

// Пример использования
interface AppState {
    user: User | null;
    posts: Post[];
    loading: boolean;
    error: string | null;
}

type AppAction = 
    | { type: "SET_USER"; payload: User }
    | { type: "SET_POSTS"; payload: Post[] }
    | { type: "SET_LOADING"; payload: boolean }
    | { type: "SET_ERROR"; payload: string | null }
    | { type: "ADD_POST"; payload: Post };

const initialState: AppState = {
    user: null,
    posts: [],
    loading: false,
    error: null
};

// Редьюсеры
const userReducer: Reducer<AppState, AppAction> = (state, action) => {
    if (action.type === "SET_USER") {
        return { ...state, user: action.payload };
    }
    return state;
};

const postsReducer: Reducer<AppState, AppAction> = (state, action) => {
    switch (action.type) {
        case "SET_POSTS":
            return { ...state, posts: action.payload };
        case "ADD_POST":
            return { ...state, posts: [action.payload, ...state.posts] };
        default:
            return state;
    }
};

const loadingReducer: Reducer<AppState, AppAction> = (state, action) => {
    if (action.type === "SET_LOADING") {
        return { ...state, loading: action.payload };
    }
    return state;
};

// Создание store
const store = new Store<AppState, AppAction>(initialState);
store.addReducer("SET_USER", userReducer);
store.addReducer("SET_POSTS", postsReducer);
store.addReducer("ADD_POST", postsReducer);
store.addReducer("SET_LOADING", loadingReducer);
```

### 10.3. Паттерн Repository с TypeScript

```typescript
// Базовый репозиторий
interface Repository<T, ID> {
    findById(id: ID): Promise<T | null>;
    findAll(): Promise<T[]>;
    save(entity: T): Promise<T>;
    update(id: ID, entity: Partial<T>): Promise<T>;
    delete(id: ID): Promise<void>;
}

// Реализация для PostgreSQL
class PostgresRepository<T extends { id: ID }, ID> implements Repository<T, ID> {
    constructor(private db: any, private tableName: string) {}
    
    async findById(id: ID): Promise<T | null> {
        const result = await this.db.query(
            `SELECT * FROM ${this.tableName} WHERE id = $1`,
            [id]
        );
        return result.rows[0] || null;
    }
    
    async findAll(): Promise<T[]> {
        const result = await this.db.query(`SELECT * FROM ${this.tableName}`);
        return result.rows;
    }
    
    async save(entity: T): Promise<T> {
        const keys = Object.keys(entity);
        const values = Object.values(entity);
        const placeholders = values.map((_, i) => `$${i + 1}`).join(", ");
        
        const result = await this.db.query(
            `INSERT INTO ${this.tableName} (${keys.join(", ")}) 
             VALUES (${placeholders}) 
             RETURNING *`,
            values
        );
        
        return result.rows[0];
    }
    
    async update(id: ID, entity: Partial<T>): Promise<T> {
        const keys = Object.keys(entity);
        const values = Object.values(entity);
        const setClause = keys.map((key, i) => `${key} = $${i + 2}`).join(", ");
        
        const result = await this.db.query(
            `UPDATE ${this.tableName} 
             SET ${setClause} 
             WHERE id = $1 
             RETURNING *`,
            [id, ...values]
        );
        
        return result.rows[0];
    }
    
    async delete(id: ID): Promise<void> {
        await this.db.query(
            `DELETE FROM ${this.tableName} WHERE id = $1`,
            [id]
        );
    }
}

// Специфичный репозиторий для пользователей
interface User {
    id: number;
    email: string;
    name: string;
    createdAt: Date;
}

class UserRepository extends PostgresRepository<User, number> {
    constructor(db: any) {
        super(db, "users");
    }
    
    async findByEmail(email: string): Promise<User | null> {
        const result = await this.db.query(
            "SELECT * FROM users WHERE email = $1",
            [email]
        );
        return result.rows[0] || null;
    }
    
    async findByName(name: string): Promise<User[]> {
        const result = await this.db.query(
            "SELECT * FROM users WHERE name ILIKE $1",
            [`%${name}%`]
        );
        return result.rows;
    }
}
```

### 10.4. Event Emitter с TypeScript

```typescript
// Типизированный EventEmitter
type EventMap = Record<string, any>;

type EventKey<T extends EventMap> = string & keyof T;
type EventReceiver<T> = (params: T) => void;

class TypedEventEmitter<T extends EventMap> {
    private listeners: {
        [K in keyof T]?: Array<EventReceiver<T[K]>>;
    } = {};
    
    on<K extends EventKey<T>>(
        eventName: K,
        listener: EventReceiver<T[K]>
    ): void {
        if (!this.listeners[eventName]) {
            this.listeners[eventName] = [];
        }
        this.listeners[eventName]!.push(listener);
    }
    
    off<K extends EventKey<T>>(
        eventName: K,
        listener: EventReceiver<T[K]>
    ): void {
        if (!this.listeners[eventName]) return;
        
        const index = this.listeners[eventName]!.indexOf(listener);
        if (index !== -1) {
            this.listeners[eventName]!.splice(index, 1);
        }
    }
    
    emit<K extends EventKey<T>>(
        eventName: K,
        params: T[K]
    ): void {
        if (!this.listeners[eventName]) return;
        
        this.listeners[eventName]!.forEach(listener => {
            listener(params);
        });
    }
    
    once<K extends EventKey<T>>(
        eventName: K,
        listener: EventReceiver<T[K]>
    ): void {
        const wrapper = (params: T[K]) => {
            listener(params);
            this.off(eventName, wrapper);
        };
        this.on(eventName, wrapper);
    }
}

// Определение событий
interface AppEvents {
    "user:login": { userId: number; timestamp: Date };
    "user:logout": { userId: number };
    "post:created": { postId: number; userId: number };
    "post:deleted": { postId: number };
    "error": { message: string; stack?: string };
}

// Использование
const eventBus = new TypedEventEmitter<AppEvents>();

eventBus.on("user:login", (data) => {
    console.log(`User ${data.userId} logged in at ${data.timestamp}`);
});

eventBus.on("error", (error) => {
    console.error("Global error:", error.message);
});

eventBus.emit("user:login", { userId: 123, timestamp: new Date() });
eventBus.emit("post:created", { postId: 456, userId: 123 });
```

### 10.5. Form Validation с TypeScript

```typescript
// Типы для валидации
type ValidationRule<T> = {
    validate: (value: T) => boolean;
    message: string;
};

type ValidationRules<T> = {
    [K in keyof T]?: ValidationRule<T[K]>[];
};

type FormErrors<T> = {
    [K in keyof T]?: string[];
};

// Класс для валидации форм
class FormValidator<T extends Record<string, any>> {
    private errors: FormErrors<T> = {};
    
    constructor(
        private rules: ValidationRules<T>,
        private data: T
    ) {}
    
    validate(): boolean {
        this.errors = {};
        let isValid = true;
        
        for (const [field, fieldRules] of Object.entries(this.rules)) {
            const value = this.data[field];
            const fieldErrors: string[] = [];
            
            if (fieldRules) {
                for (const rule of fieldRules) {
                    if (!rule.validate(value)) {
                        fieldErrors.push(rule.message);
                        isValid = false;
                    }
                }
            }
            
            if (fieldErrors.length > 0) {
                this.errors[field as keyof T] = fieldErrors;
            }
        }
        
        return isValid;
    }
    
    getErrors(): FormErrors<T> {
        return this.errors;
    }
    
    getFieldError(field: keyof T): string | null {
        const fieldErrors = this.errors[field];
        return fieldErrors && fieldErrors.length > 0 ? fieldErrors[0] : null;
    }
    
    hasErrors(): boolean {
        return Object.keys(this.errors).length > 0;
    }
}

// Предопределенные правила валидации
const ValidationRules = {
    required: <T>(message = "Это поле обязательно"): ValidationRule<T> => ({
        validate: (value) => value !== null && value !== undefined && value !== "",
        message
    }),
    
    minLength: (min: number, message?: string): ValidationRule<string> => ({
        validate: (value) => value.length >= min,
        message: message || `Минимальная длина ${min} символов`
    }),
    
    maxLength: (max: number, message?: string): ValidationRule<string> => ({
        validate: (value) => value.length <= max,
        message: message || `Максимальная длина ${max} символов`
    }),
    
    email: (message = "Некорректный email"): ValidationRule<string> => ({
        validate: (value) => /^[^\s@]+@([^\s@]+\.)+[^\s@]+$/.test(value),
        message
    }),
    
    pattern: (regex: RegExp, message: string): ValidationRule<string> => ({
        validate: (value) => regex.test(value),
        message
    }),
    
    custom: <T>(validate: (value: T) => boolean, message: string): ValidationRule<T> => ({
        validate,
        message
    })
};

// Пример использования
interface LoginForm {
    email: string;
    password: string;
    rememberMe: boolean;
}

const loginRules: ValidationRules<LoginForm> = {
    email: [
        ValidationRules.required("Email обязателен"),
        ValidationRules.email("Введите корректный email")
    ],
    password: [
        ValidationRules.required("Пароль обязателен"),
        ValidationRules.minLength(6, "Пароль должен содержать минимум 6 символов"),
        ValidationRules.maxLength(50, "Пароль слишком длинный")
    ],
    rememberMe: [
        ValidationRules.custom<boolean>(
            (value) => true, // Всегда валидно
            ""
        )
    ]
};

const formData: LoginForm = {
    email: "test@example",
    password: "123",
    rememberMe: true
};

const validator = new FormValidator(loginRules, formData);
if (!validator.validate()) {
    console.log("Ошибки валидации:", validator.getErrors());
    // { email: ["Введите корректный email"], password: ["Минимальная длина 6 символов"] }
}
```

---

## Заключение

TypeScript — это мощный инструмент, который значительно улучшает качество и поддерживаемость JavaScript-кода. Основные преимущества:

1. **Статическая типизация** — обнаружение ошибок на этапе разработки
2. **Лучшая поддержка IDE** — автодополнение, рефакторинг, навигация
3. **Самодокументируемый код** — типы служат документацией
4. **Современные возможности** — декораторы, generics, утилитарные типы
5. **Масштабируемость** — легче поддерживать и развивать большие проекты

### Рекомендации для начала работы:

1. Начните с `strict: true` в tsconfig.json
2. Используйте `unknown` вместо `any`
3. Применяйте утилитарные типы для преобразования существующих типов
4. Используйте `interface` для объектов и `type` для сложных конструкций
5. Пишите type guards для сужения типов
6. Используйте декораторы для cross-cutting concerns

TypeScript — это не просто "JavaScript с типами", это полноценный язык, который помогает писать более надежный и поддерживаемый код.
