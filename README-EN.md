# Angular-Interview-Questions

##### 1. Constructor is a special method used to create and initialize objects created using class. <br><br>

##### 2. The main components of the angular ?
- `Directive`
- `Module`
- `Service`
- `Component`
- `Guard`
- `Pipe`
<br><br>

##### 3. What is interpolation in Angular? <br>
Interpolation markup with embedded expressions is used in Angular to assign data to text nodes and attribute values. Например: <br>
`<a href="img/{{username}}.jpg">Hello {{username}}!</a>` <br><br>

##### 4. What is Data Binding ?
- Angular supports one-way and two-way Data Binding. This is a mechanism for coordinating parts of a template with parts of a component.
Adding special markup tells Angular how to bind both sides. The following diagram shows the four forms of data binding.
One-way:
From component to DOM with value binding: {{hero.name}}
From component to DOM with property binding and value assignment: [hero]="selectedHero"
From DOM to component with event binding: (click)="selectHero(hero)"

Two-way data binding is mostly used in template-driven forms, combining parameter and event. Here's an example using a binding with ngModel directive.
`<input [(ngModel)]="hero.name">`.

Here the value comes into the input from the component, just like with binding, but when the user changes the value, the new value is passed to the component and overridden
<br><br>

##### 5. What is a promise ? <br>
Promise - object is used for delayed and asynchronous calculations. <br>
The result of an operation that is not yet complete, but will be at some indefinite point in the future.
<br><br><br>

##### 6. The basic principles of the OOP
- Encapsulation
- Abstraction
- Polymorphism
- Inheritance
<br><br>
 
##### 7. What is Directive ? Module ? Service ? Component ? Pipe ? Guard ? <br>

- An Angular module is a class with the @NgModule() decorator that serves as an isolating logical unifying structure for components, directives, filters, and services. All of the listed entities are defined and configured with @NgModule().
- <br>
- Guards allow you to restrict navigation along certain routes
- <br>
- A service is a class with a narrow, well-defined purpose. It can be a value, a function, a request, etc. The main thing about them is that they are reusable, separating out the pure functionality of the component.
- <br>
- Pipes transform the display of values in a template, for example displaying dates in different locales or changing the case of strings in the display. <br><br>

##### 8. What are the directives? What do they do? <br>
- Structure directives affect the DOM and can add/remove elements (ng-template, NgIf, NgFor, NgSwitch, etc)<br>
- Attribute directives change the appearance or behavior of elements, components or other directives (NgStyle, NgClass, etc)<br><br>

##### 9. What is a decorator and what types of decorators do you know? <br>
A decorator is a way to add metadata to a class declaration. It is a special kind of declaration that can be attached to a class declaration, method, access method, property, or parameter. <br>
Decorators use the form @expression, where expression is the function that will be called at runtime with information about the decorated declaration.

To write our own decorator, we need to make it a factory and define its type:<br>
- ClassDecorator
- PropertyDecorator
- MethodDecorator
- ParameterDecorator
<br><br>

##### 10. NGRX

- ngrx is a group of libraries "inspired by" the Redux library, which in turn is "inspired by" the Flux template. This means that the Redux template is a simplified version of the Flux template, and NGRX is a version of the redux template using Angular and RxJS.

- Store...<br>
A store is an object (an instance of the ngrx/Store class) that combines the things we mentioned earlier (actions, reducers, selectors). For example, when an action is sent through its functions, the store finds and executes the corresponding reducer.
It also stores the state of the application. <br><br><br>

##### 11. What kind of flow ? - (action -> effect -> reducer)

- 1.
###### Actions<br><br>
Actions: A unique event sent from components and services that describes how the state is to be changed. For example, "Add Client" might be an action that changes the state (i.e., adds a new client to the list).
<br>
In a store object you have a function to send/run (dispatch/trigger) actions. Actions are classes that implement the NGRX/Actions action interface. These action classes have two properties (let's take as an example the action class named GetUserName):
type: this is a plain read-only string that describes what the action means. For example: '[User] Get User Name'.
Payload: the type of this property depends on what kind of data this action needs to send to the reducer. In the case of the previous example this will be a string containing the user name. Not all actions require payload. <br><br>
- 2.
If the action caused an effect, it indicates that you need to handle the side effects before calling the reducer. This could be something like calling the HTTP service to retrieve data. <br><br>
###### Effects
Effects: A mechanism that listens for dispatching actions in the observed stream, processes the server response, and returns new actions either immediately or asynchronously to the reducer to change state.
The effects listen for the sent actions, and, just like the reducers, check to see if they have a handler for them. The side effect is then performed. Typically, this is receiving or sending data via an API.
Then the next action will be executed, usually related to the resulting state of the side effect (success, data sending error, etc.). The action is then processed by the reducer.<br><br>
- 3.
If the action does not trigger effect, the reducer will filter the action (usually using the switch operator) and return a new state, which will be the result of merging the old state with the value that changed after the action was called.
###### Reducers
Reducer: All state changes take place inside the reducer; it reacts to an action and creates a new immutable state based on that action and returns it to the repository.

Reducers are pure functions that take two arguments: the previous state (state) and the action (action). When an action is sent, ngrx goes through all reducers, passing the previous state and action as arguments, in the order in which the reducers were created, until it finds a handler for that action.
- 4.
###### Selectors
Selector is a function used to retrieve a piece of state from the repository.

They allow us to handle the state fragment data outside the component. The "select" function of the repository takes a pure function as an argument, it is our selector.

<br><br>

##### 12. What is Singleton Service and why do they use it in Angular?
- These are services declared in the application and have one instance for the entire application
<br><br>

##### 13. How to make a Singleton service ?
- Declare it @Injectable(root)
- Include it in an AppModule in providers, or in a single module imported into an AppModule.
<br><br>

##### 14. What is Observable ?
- Observable is an observer that subscribes and responds to all events up to the point of unsubscribing. <br><br>

##### 15. What is Dependency Injection? <br>
This is an important pattern in application design. In Angular, the implementation of dependencies is implemented from under the hood. <br>
Dependencies are services or objects that the class needs to perform its functions. DI - allows you to request dependencies from external sources. <br><br><br>

##### 16. What is the difference between Observable and Promise?
- Promise handles one value at the end of an asynchronous operation, regardless of its outcome, and does not support undoing the operation.
- Observable, on the other hand, is a thread, and allows you to pass both zero and multiple events when the callback is called for each event.
<br><br>

##### 17. What is the difference between `Observable` and `BehaviorSubject/Subject` (Higher Order Observables) ?
- Subjects are special Observable. Imagine there is a speaker with a microphone who speaks in a room full of people. These are the Subjects and their message is sent to several recipients at once. The regular Observables are like a 1 on 1 conversation. A Subject is multicast, i.e. can pass a message to several recipients at once.
- BehavioralSubject - requires an initial value and passes the current value to new subscriptions.

##### 18. What is the difference between `Subject`, `BehaviorSubject`, `ReplaySubject`, `AsyncSubject` ?
- Subject` - does not store its previous states, the viewer gets information only when the Subject generates a new event using the .next() method.
- BehavioralSubject` - when subscribed, the behavioral Subject notifies its viewer of the last event that occurred in it or, if no event occurred in the Subject, creates an event for the viewer with the original information that is passed when the Subject is created.
- ReplaySubject' - when subscribed, a repeating Subject notifies its new viewer of all the events that have occurred in it since it was created. To optimize, when creating a repeating Subject, it is possible to pass a number of recent events which will be repeated for each new viewer. It should be noted that creating a ReplaySubject with a number of repeating events equal to 1 is equivalent to creating a BehaviorSubject.
- An `AsyncSubject` - asynchronous Subject notifies its viewers only about the last event that occurred and only when the Subject successfully completes. If `AsyncSubject` ends with an error, its viewers will be notified only about the error.
<br><br>

##### 19. What is Change Detection, how does the Change Detection Mechanism work?
- `Change Detection` - процесс синхронизации модели с представлением. In Angular, the flow of information is unidirectional, even when using ngModel to implement two-way binding, which is syntactic sugar on top of the unidirectional flow. <br>
- The `Change Detection Mechanism` - only moves forward and never looks back, starting from the root (root) component to the last. That's the point of one-way data flow. The architecture of an Angular application is very simple - a component tree. Each component points to a child, but the child does not point to the parent. One-way flow eliminates the need for a $digest loop.
<br><br>

##### 20. What are the strategies for detecting changes? <br>
- There are two strategies in total - `Default` and `OnPush`. If all components use the first strategy, Zone checks the entire tree regardless of where the change occurred. To tell Angular that we will comply with the performance improvement conditions we need to use the OnPush change detection strategy. This will tell Angular that our component depends only on input data and any object that is passed to it should be considered immutable. This is all built on the principle of the Mili automaton, where the current state depends only on the input values. <br><br>

##### 21. Tell us about OnPush Change Detection Strategy
- On push change detection means that change detection in a component is only run when the input data changes, and when the input data changes the whole object must change. This means that if only a reference is changed, change detection will not be triggered.
<br><br>

##### 22. What is ViewEncapsulation ?
ViewEncapsulation determines whether the template and styles defined in a component can affect the entire application or vice versa. All components with None encapsulation will have their styles duplicated in all components with their own encapsulation.
<br><br>
- `ShadowDom` - Angular uses the browser's built-in Shadow DOM API to enclose the component's view inside a ShadowRoot, used as the component's host element, and apply the provided styles in an isolated manner.
- `Emulated` - Angular modifies the component's CSS selectors so that they are only applied to the component's view and do not affect other elements in the application, emulating Shadow DOM behavior.
- 'None' - Angular does not apply any sort of view encapsulation meaning that any styles specified for the component are actually globally applied and can affect any HTML element present within the application. This mode is essentially the same as including the styles into the HTML itself.

<br><br>

##### 23. What is Shadow DOM in angular?
The Shadow DOM is like a parallel DOM tree placed inside a component (an HTML element, not to be confused with Angular components) hidden from the main DOM tree. No part of the application has access to this shadow DOM other than the component itself.

<br><br><br>

##### 24. What are HTTP Interceptors?
- Interceptor is just a fancy word for a function that gets requests/responses before they are processed/sent to the server. You should use interceptors if it makes sense to pre-process many types of requests in one way. For example, it is necessary to set an authorization header for all requests
<br><br><br>

##### 25. What is routing and how to create it in Angular?
Роутинг позволяет реализовать навигацию от одного view приложения к другому при работе пользователя с приложением.
Это реализовано через взаимодействие с адресной строкой, Angular Router интерпретирует ее как инструкцию по переходу между view. Возможна передача параметров вспомогательному компоненту для конкретизирования предоставляемого контента. Навигация может осуществлять по ссылкам на странице, кнопкам или другим элементам, как кнопки "вперед-назад" в браузере.
Для создания роутинга первым делом необходимо импортировать "RouterModule" и "Routes" в AppModule.
Затем необходимо реализовать конфигурацию по приложению, определить path и относящие к ним компоненты, и в метод RouterModule.forRoot() передать конфигурацию.
Наконец необходимо добавить routerLink в шаблон.
<br><br><br>

##### 26. Расскажите про lazy load и как оно работает ?
Ленивая загрузка - это метод в Angular, который позволяет загружать компоненты JavaScript асинхронно при активации определенного маршрута. Это увеличивает скорость загрузки приложения за счет разделения приложения на несколько пакетов. Когда пользователь перемещается по приложению, пакеты загружаются по мере необходимости. <br>
Ленивая загрузка в целом - это концепция, при которой мы откладываем загрузку объекта до тех пор, пока он не понадобится. В Angular все компоненты JavaScript, объявленные в массиве объявлений app. модуль. ts объединяются и загружаются одним махом, когда пользователь посещает наш сайт.
<br>
Преимущества: производительность и размер
<br><br>

##### 27. Что такое ElementRef, TemplateRef
Основная и самая часто используемая абстракция - ElementRef. Она хранит в себе "оригинальный" HTML-элемент в свойстве nativeElement так, если бы он был получен с помощью нативного JavaScript.
<br>
Ранее уже упоминалось, что ссылка типа `TemplateRef` возвращается в том случае, если запрос возвращает представление, заключенное в специальные теги `<ng-template />`.

Класс TemplateRef содержит единственное свойство `elementRef`, содержащее экземпляр класса `ElementRef`, который в свою очередь ссылается на host-элемент.

##### 28. Что такое JIT и AOT, в чем их отличия и каковы сферы применения?
Angular приложение можно скомпилировать с помощью команд ng serve и ng build. При этом, можно работать с разными видами компиляции:

- JIT - (Just-In-Time compilation) - компиляция "на лету", динамическая компилияция. В Angular используется по умолчанию.
- AOT - (Ahead-Of-Time compilation) - компиляции перед исполнением.
