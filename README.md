# Angular-Interview-Questions

##### 1. Constructor - специальный метод, служащий для создания и инициализации объектов, созданных с использованием class. <br>
##### 2. Основные составляющие ангуляра ?
- `Directive`
- `Module`
- `Service`
- `Component`
- `Guard`
- `Pipe`
<br>

##### 3. Что такое интерполяция в Angular? <br>
Разметка интерполяции с внедренными выражениями используется в Angular для присвоение данных текстовым нодам и значения аттрибутов. Например: <br>
`<a href="img/{{username}}.jpg">Hello {{username}}!</a>`
<br>

##### 4. Что такое Data Binding ?
- Angular поддерживает одностороннюю и двустороннюю Data Binding. Это механизм координации частей шаблона с частями компонента.
Добавление специальной разметки сообщает Angular как соединять обе стороны. Следующая диаграмма показывает четыре формы привязки данных.
Односторонние:
От компонента к DOM с привязкой значения: {{hero.name}}
От компонента к DOM с привязкой свойства и присвоением значения: [hero]="selectedHero"
От DOM к компоненту с привязкой на ивент: (click)="selectHero(hero)"
Двусторонняя в основном используется в template-driven forms, сочетает в себе параметр и ивент. Вот пример, использующий привязку с директивой ngModel.
`<input [(ngModel)]="hero.name">`
Здесь значение попадает в input из компонента, как при привязке значения, но при изменении юзером значения новое передается в компонент и переопределяется
<br>

##### 5. Что такое promise ? <br>
Promise — это объект в JavaScript, который представляет собой значение, которое может быть доступно сейчас, позже или никогда. Он используется для работы с асинхронными операциями. Promise может находиться в одном из трёх состояний:<br>

Pending (ожидание) — начальное состояние, когда операция ещё не завершена.
Fulfilled (выполнено) — операция завершена успешно, и Promise содержит результат.
Rejected (отклонено) — операция завершена с ошибкой, и Promise содержит причину отказа (ошибку).

<br><br>
Можно ли отменить Promise?
Стандартный объект Promise в JavaScript не поддерживает отмену. После того как промис был создан, он либо выполнится успешно, либо отклонится. Но вы не можете "прервать" или "отменить" его выполнение.

Однако, есть несколько подходов для реализации отмены асинхронной операции:

1) Использование AbortController (в браузерах и некоторых средах выполнения): Это современный способ отмены асинхронных операций, таких как запросы через fetch.
2) Реализация собственной логики отмены с использованием Promise: Можно создать обёртку вокруг Promise, которая будет поддерживать отмену. Например, с помощью флага или дополнительного состояния.

<br><br><br>

### Callback (Колбэк)
Это функция, которая передаётся в другую функцию как аргумент и вызывается после завершения асинхронной операции.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Данные получены");
  }, 1000);
}

fetchData((message) => {
  console.log(message); // "Данные получены"
});
```

### Promise (Промис)
Это объект, который представляет собой промежуточное состояние асинхронной операции. Промис может быть в одном из трёх состояний: ожидает (pending), исполнен (fulfilled), отклонён (rejected).

```javascript
let promise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("Операция успешна");
  } else {
    reject("Произошла ошибка");
  }
});

promise
  .then(result => console.log(result))  // "Операция успешна"
  .catch(error => console.log(error));  // Если ошибка
```

### async/await
async/await — это синтаксический сахар, который позволяет работать с промисами так, как будто это синхронный код, улучшая читаемость. async делает функцию асинхронной, а await позволяет "подождать" завершения промиса.

```javascript
async function fetchData() {
  let result = await new Promise(resolve => setTimeout(() => resolve("Данные получены"), 1000));
  console.log(result); // "Данные получены"
}

fetchData();
```


##### 6. Основные принципы ООП
  Инкапсуляция
  Абстракция
  Полиморфизм
  Наследование
  <br><br>
 
##### 7. Что такое Directive ? Module ? Service ? Component ? Pipe ? Guard ? <br>

- Angular модуль - это класс с декоратором @NgModule(), который служит изолирующей логической объединяющей структурой для компонентов, директив, фильтров и сервисов. Все перечисленные сущности определяются и конфигурируются с помощью @NgModule(). <br>
- Guards позволяют ограничить навигацию по определенным маршрутам. <br>
- Сервис это класс с узкой, четко определенной целью. Это может быть значение, функция, запрос, etc. Главное в них то, что они повторно используются, отделяя чистую функциональность компонента.<br><br>
- Пайп преобразует отображение значений в шаблоне, к примеру отображение дат в разных локалях или изменяют в отображении регистр строк. <br><br>
<br><br>

##### 8. Какие бывают директивы ? Что они делают ? <br>
- Компонентные. С собственным шаблоном, или по-другому компоненты (компоненты являются директивами);
- Структурные директивы влияют на DOM и могут добавлять/удалять элементы (ng-template, NgIf, NgFor, NgSwitch, etc) <br>
- Атрибутные директивы меняют внешний вид или поведение элементов, компонентов или других директив (NgStyle, NgClass, etc). <br>
<br><br>

##### 9. Что такое декоратор и какие виды декораторов вы знаете? <br>
Декоратор - способ добавления метаданных к объявлению класса. Это специальный вид объявления, который может быть присоединен к объявлению класса, методу, методу доступа, свойству или параметру. <br>
Декораторы используют форму @expression, где expression - функция, которая будет вызываться во время выполнения с информацией о декорированном объявлении.

Чтобы написать собственный декоратор, нам нужно сделать его factory и определить тип: <br>
- `Class decorators`, которые используются для добавления функциональности в класс, например, @Component и @NgModule
- `Property decorators` для добавления функциональности к свойствам внутри классов, например, @Input и @Output
- `Method decorators` для методов внутри классов, например @HostListener
- `Parameter decorators` для параметров внутри конструкторов классов, например, @Inject
<br><br>

##### 10. NGRX

- ngrx — это группа библиотек, «вдохновленная» библиотекой Redux , которая, в свою очередь, «вдохновлена» шаблоном Flux . Это означает, что шаблон Redux является упрощенной версией шаблона Flux , а NGRX является версией шаблона redux с использованием Angular и RxJS.

- Хранилище (store)… <br>
Хранилище — это объект (экземпляр класса ngrx/Store), который объединяет вещи, о которых мы упоминали ранее (действия, редукторы, селекторы). Например, когда через его функции отправляется действие,то хранилище находит и выполняет соответствующий редуктор.
Оно также хранит состояние приложения. <br><br>
<br>

##### 11. Какой флоу ? (action -> effect -> reducer)

- 1.
###### Действия (actions)<br><br>
Действие: Уникальное событие, отправляемое из компонентов и служб, которое описывает, как должно быть изменено состояние. Например, "Добавить клиента" может быть действием, которое изменит состояние (т.е. добавит нового клиента в список).
<br>
В объекте хранилища (store object) у вас есть функция для отправки/запуска (dispatch/trigger) действий. Действия — это классы, которые реализуют интерфейс действий NGRX/Actions. Эти классы действий имеют два свойства (давайте возьмем в качестве примера класс действия с именем GetUserName):
тип (type): это обычная строка только для чтения, описывающая, что означает действие. Например: ‘[User] Get User Name’
Полезная нагрузка (payload): тип этого свойства зависит от того, какой тип данных это действие необходимо отправить редуктору (reducer). В случае с предыдущим примером это будет строка, содержащая имя пользователя. Не все действия требуют полезной нагрузки. <br><br>
- 2.
Если действие вызвало эффект, то это говорит о необходимости обработки побочных эффектов перед вызовом редуктора. Это может быть что-то вроде вызова службы HTTP для получения данных. <br><br>
###### Эффекты (effects)
Эффект: Механизм, который слушает диспетчеризацию действий в наблюдаемом потоке, обрабатывает ответ сервера и возвращает новые действия либо сразу, либо асинхронно редуктору для изменения состояния.
Эффекты прослушивают отправленные действия, и, также как и редукторы, проверяют, имеются ли у них обработчик для них. Затем выполняется побочный эффект. Обычно это получение или отправка данных посредством API.
Потом будет выполнено следующее действие, обычно относящееся к результирующему состоянию побочного эффекта (успех, ошибка отправки данных, и т. д.). Затем действие обрабатывает редуктор.<br><br>
- 3.
Если действие не вызывает эффект (trigger effect), то редуктор отфильтрует действие (обычно с помощью оператора switch), и вернёт новое состояние, которое будет результатом слияния старого состояния со значением, которое изменилось после вызова действия.
###### Редукторы (reducers)
Редуктор: Все изменения состояния происходят внутри редуктора; он реагирует на действие и на основе этого действия создает новое неизменяемое состояние и возвращает его в хранилище.

Редукторы — это чистые функции, принимающие два аргумента: предыдущее состояние (state) и действие (action). Когда отправляется действие, ngrx проходит через все редукторы, передавая в качестве аргументов предыдущее состояние и действие, в порядке, в котором редукторы были созданы, пока не найдет обработчик для этого действия.
- 4.
###### Селекторы (select)
Селектор: Selector - это функция, используемая для получения части состояния из хранилища.
Они позволяют нам обрабатывать данные фрагмента состояния вне компонента. Функция «select» хранилища принимает в качестве аргумента чистую функцию, она и является нашим селектором.

<br><br>

##### 12. Что такое Singleton Service и с какой целью его используют в Angular ?
- Это сервисы, объявленные в приложении и имеющие один экземляр на все приложение
<br><br>

##### 13. Как сделать сервис Singleton ?
- Объявить его @Injectable(root)
- Включить его в AppModule в providers, либо в единственный модуль импортируемый в AppModule.
<br><br>

##### 14. Что такое Observable ?
`Observer` (наблюдатель) — это объект-обработчик потока данных, который ему передает Observable.

`Observable` (наблюдаемый) — это объект-передатчик потока данных, их существует 2 типа:

`Cold` — начинает потоковую передачу данных после вызова subscribe().
`Hot` — передается сразу после его создания, даже если ни один подписчик не заинтересован в данных.
Observables выполняют 3 основных действия:

передача следующего элемента;
сообщение об ошибке;
уведомление о завершении потоковой передачи.
`Observer` же, в свою очередь, для обработки вышеуказанных действий использует 3 функции:

- `next()` — обработка следующего элемента;
- `error()` — обработка ошибок;
- `complete()` — вызов после завершения потока данных.

- `Observables` может быть отменено.
- `Observables` можно повторить (retry и retryWhen), и это легко сделать, в отличие от Promises.
 
<br><br>

##### 15. Что такое Dependency Injection? <br>
Это важный паттерн шаблон проектирования приложений. В Angular внедрение зависимостей реализовано из-под капота. <br>
Зависимости - это сервисы или объекты, которые нужны классу для выполнения своих функций. DI -позволяет запрашивать зависимости от внешних источников. <br><br>
<br><br>

##### 16. В чём разница между Observable и Promise ?
- Promise обрабатывает одно значение по завершению асинхронной операции, вне зависимости от ее исхода, и не поддерживают отмену операции.
- Observable же является потоком, и позволяет передавать как ноль, так и несколько событий, когда callback вызывается для каждого события.
<br><br>

##### 17. В чём разница между `Observable` и `BehaviorSubject/Subject` (Higher Order Observables) ?
- Subjects - специальные Observable. Представьте, что есть спикер с микрофоном, который выступает в комнате, полной людей. Это и есть Subjects, их сообщение передается сразу нескольким получателям. Обычные же Observables можно сравнить с разговором 1 на 1. Subject - является multicast, то есть может передавать значение сразу нескольким подписчикам.
- BehaviorSubject - требует начальное значение и передает текущее значение новым подпискам.

##### 18. В чем разница между `Subject`, `BehaviorSubject`, `ReplaySubject`, `AsyncSubject` ?
- `Subject` - не хранит свои предыдущие состояния, зритель получает информацию только тогда, когда Subject сгенерирует новое событие, используя метод .next().
- `BehaviorSubject` - при подписке поведенческий Subject уведомляет своего зрителя о последнем произошедшем в нём событии или, если в Subject-е не происходило событий, создаёт для зрителя событие с изначальной информацией, которая передаётся при создании Subject-а.
- `ReplaySubject` - при подписке повторяющийся Subject уведомляет своего нового зрителя о всех произошедшем в нём событиях с момента создания. Для оптимизации при создании повторяющегося Subject-а можно передать число последних событий, которые будут повторяться для каждого нового зрителя. Стоит отметить, что создание ReplaySubject-а c числом повторяющихся событий равное 1 эквивалетно созданию BehaviorSubject-а.
- `AsyncSubject` - асинхронный Subject уведомляет своих зрителей только о последнем произошедшем событии и только когда Subject успешно завершается. Если `AsyncSubject` завершится ошибкой, его зрители будут уведомлены только об ошибке.

<br><br>

##### 19. Что такое Change Detection, как работает Change Detection Mechanism?
- `Change Detection` - процесс синхронизации модели с представлением. В Angular поток информации однонаправленный, даже при использовании ngModel для реализации двустороннего связывания, которая является синтаксическим сахаром поверх однонаправленного потока. <br>
- `Change Detection Mechanism` <br>
`Change Detection Mechanism` - продвигается только вперед и никогда не оглядывается назад, начиная с корневого (рут) компонента до последнего. В этом и есть смысл одностороннего потока данных. Архитектура Angular приложения очень проста — дерево компонентов. Каждый компонент указывает на дочерний, но дочерний не указывает на родительский. Односторонний поток устраняет необходимость $digest цикла.
<br><br>

##### 20. Какие существуют стратегии обнаружения изменений? <br>
- Всего есть две стратегии - `Default` и `OnPush`. Если все компоненты используют первую стратегию, то Zone проверяет все дерево независимо от того, где произошло изменение. Чтобы сообщить Angular, что мы будем соблюдать условия повышения производительности нужно использовать стратегию обнаружения изменений OnPush. Это сообщит Angular, что наш компонент зависит только от входных данных и любой объект, который передается ему должен считаться immutable. Это все построено на принципе автомата Мили, где текущее состояние зависит только от входных значений.
- A zone is an execution context that persists across async tasks. You can think of it as thread-local storage for the JavaScript VM
<br><br>

##### 21. Расскажите про OnPush Change Detection Strategy
- On push change detection означает, что обнаружение изменений в компоненте выполняется только при изменении входных данных, а при изменении входных данных должен измениться весь их объект. Это означает, что если изменяется только ссылка, то обнаружение изменений не будет запущено.
<br><br>

##### 22. Что такое ViewEncapsulation ?
ViewEncapsulation определяет, могут ли шаблон и стили, определенные в компоненте, влиять на все приложение или наоборот. Все компоненты с инкапсуляцией None будут иметь свои стили, дублированные во всех компонентах с собственной инкапсуляцией.
<br><br>
- Инкапсуляция представления ShadowDom использует собственную реализацию теневой DOM браузера для присоединения теневой DOM к элементу узла компонента, а затем помещает представление компонента внутри этой теневой DOM. Стили компонента включены в теневой DOM.
- Эмулированная инкапсуляция представления (по умолчанию) имитирует поведение теневой модели DOM путем предварительной обработки (и переименования) кода CSS для эффективного применения CSS к представлению компонента.
- Нет означает, что Angular не выполняет инкапсуляцию представления. Angular добавляет CSS к глобальным стилям. Обсуждаемые ранее правила определения объема, изоляции и защиты не применяются. По сути, это то же самое, что и вставка стилей компонента в HTML.

<br><br>

##### 23. Что такое Shadow DOM в angular?
Shadow DOM подобен параллельному дереву DOM, размещенному внутри компонента (элемент HTML, не путать с компонентами Angular), скрытого от основного дерева DOM. Никакая часть приложения не имеет доступа к этой теневой DOM, кроме самого компонента.

<br><br><br>

##### 24. Что такое HTTP Interceptors?
- Interceptor (перехватчик) - просто причудливое слово для функции, которая получает запросы / ответы до того, как они будут обработаны / отправлены на сервер. Нужно использовать перехватчики, если имеет смысл предварительно обрабатывать многие типы запросов одним способом. Например нужно для всех запросов устанавливать хедер авторизации
<br><br><br>

##### 25. Что такое роутинг и как его создать в Angular?
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

##### 29. Каков механизм жизненного цикла компонента в Angular?
- `ngOnChanges`: вызывается при изменении входного свойства компонента.
- `ngOnInit`: вызывается после первого ngOnChanges.
- `ngDoCheck`: вызывается во время каждого цикла обнаружения изменений.
- `ngAfterContentInit`: вызывается после инициализации содержимого компонента.
- `ngAfterContentChecked`: вызывается после каждой проверки содержимого компонента.
- `ngAfterViewInit`: вызывается после инициализации представлений компонента.
- `ngAfterViewChecked`: вызывается после каждой проверки представлений компонента.
- `ngOnDestroy`: вызывается непосредственно перед удалением компонента.

##### 30. Что такое внедрение зависимостей и как оно используется в Angular?
Внедрение зависимостей — это шаблон проектирования, который позволяет компоненту получать зависимости от отдельного поставщика. Этот шаблон используется в Angular для внедрения сервисов, конвейеров и других зависимостей в компоненты и другие части приложения.

