# FRONTEND
## Технический стек
- Typescript 
- React
- [React-router-dom](https://reactrouter.com/en/main) (Роутинг)
- [ky](https://github.com/sindresorhus/ky#readme) (fetch запросы)
- [rechart](https://recharts.org/en-US/api) (отрисовка графиков)
- [clsx](https://github.com/lukeed/clsx#readme) (условного построения строк в className)
- [react-icons/md](https://react-icons.github.io/react-icons/icons?name=md) (иконки )
- [Framer Motion](https://www.framer.com/motion/introduction/) (анимация)
- [sass](https://sass-lang.com/documentation/) (модульные стили)
- [Zustand](https://github.com/pmndrs/zustand) (стейт менеджер)
- EsLint (линтер)
- [generate-react-cli](https://github.com/arminbro/generate-react-cli#readme) (создание templates)
- [JSON-server](https://github.com/typicode/json-server#readme) (сервер с MOCK данными)
- [tanstac](https://tanstack.com/query/v5/docs/react/overview) (выборка, кэширование, синхронизация и обновление состояния сервера)


## Структура проекта
- src
	- [api](#api)
	- [assets](#assets)
	- [components](#components)
		- ui
	- [hooks](#hooks)
	- [hocs](#hocs)
	- [pages](#pages)
	- [styles](#styles)
	- App.tsx
	- main.tsx
	- [router.tsx](#router.tsx)
	- vite-env.d.ts
- [templates](#templates)
	- components
	- pages
	- ui

### api
служит для хранения эндпоинтов и инстансов запросов.
структура следующая:
* **index.ts** - для быстрого импорта
    `export * from ky.ts`
* **ky.ts** - хранение инстансов
	`export const http = ky.extend({...}})`
* **endpoints.ts** - хранение эндпоинтов
	`ENDPONTIS{
		USER:"/user"
	}`
* **[name-route]** - логика отправки
	`export const getUser = (options)=> await http.get(ENDPOINTS.USER, options)`

### assets
хранение статическиз файлов
### components

**создание компонента**
<code> <b><i>console</i></b>
npm run c <название>
npm run c <название1> <название2>
</code>

**создание UI компонента**
<code> <b><i>console</i></b>
npm run ui <название>
npm run ui <название1> <название2>
</code>

дериктория служит для хранение компонентов
следует создовать компонент если он встречается больше **1 раза**
Также присутвует папкв **ui**. Она служит для создания базовых низкоуровневых компонентов таких как: 
* Autocomplete
* Avatar
* Badge
* Button
* Button Group
* Checkbox
* Chip
* Divider
* Input
* Link
* List
* Radio Button
* Select
* Slider
* Switch
* Table
* Tabs
* Textarea
* Tooltip




### hooks
создание пользовательских хуков
### hocs
создание пользовательских компонентов вышего порядка
### pages
**создание страницы**
<code> <b><i>console</i></b>
npm run p <название>
npm run p <название1> <название2>
</code>

дериктория служит для страниц
по максимуму не использовать состояния на страницах, а выносить в отдельный компонент
### styles
Хранение базовых стилий и стилий с переменными
### router.tsx
роутинг 
### templates
хранение шаблонов создания
## Импорты
вот так импорты выглядят:
`@/components/name`
`@/page/name`
`@/styles/name`
`@/api/name`
....

работает автоимпорт

для упрощения работы с испортами абсолютных адресов, были записаны следющие правила:

<pre><code><i>//vite.config.ts</i>
...
resolve: {
	alias: [{ find: '@', replacement: path.resolve(__dirname, 'src') }]
}
</code></pre>
<pre><code><i>//tsconfig.json</i>
...
"baseUrl": ".",
"paths": {
	"@/*": ["./src/*"]
}
</code></pre>
## Стили
### Sass
все стили стили должны быть модулями
`import s from "./name.module.scss"`

класс корневого рордителя JSX елемента должен называться root
`<div className={s.root}> ...  </div>`
<pre><code><i>//name.module.scss</i>

<b>.root{
	.element{...}
	...
}</b></code></pre>

для работы с переменными подключается через дерективу `@use`. В `.scss` файл абсолютный импорт не работает.
<pre><code><i>//name.module.scss</i>
<b>@use "../../styles/varable.scss" as v;</b>

.root{
	background: <b>v.$bgColor</b>;
	...
}
</code></pre>

### шрифты
Начертания шрифтов заранее заготовлены в виде классов. Название должны быть с сответствием дизайн проекта в Figma, только переписаны camelCase.
<pre><code><i>//Figma</i>
main_text * 16/20
</code></pre>
<pre><code><i>//name.tsx</i>
...
 < Element  className=<b>"mainText"</b> ...>
</code></pre>
Используйте с библиотекой `clsx` для добавления класса или условия:
</code></pre>
<pre><code><i>//name.tsx</i>
<b>import cslx from 'clsx'</b>
...
<b>const [active,setActive] = useState< boolean >(false)</b>
...
 < Element  className= {<b>clsx([s.root, "mainText", active && s.active</b>])} ...>
</code></pre>

## Расширения для помощи
- [Figma for VS Code](https://marketplace.visualstudio.com/items?itemName=figma.figma-vscode-extension)
- [Git Graph](Git%20Graph)
- [Postman](https://marketplace.visualstudio.com/items?itemName=Postman.postman-for-vscode)
- [SCSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-scss)

