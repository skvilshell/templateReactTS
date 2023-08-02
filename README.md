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
  <code>export * from ky.ts</code>
* **ky.ts** - хранение инстансов
```typescript
export const http = ky.extend({...}})
```
* **endpoints.ts** - хранение эндпоинтов
```typescript
ENDPONTIS: {
	USER:"/user"
}
```
* **[name-route]** - логика отправки
```typescript
export const getUser = (options)=> await http.get(ENDPOINTS.USER, options)
```

### assets
хранение статическиз файлов
### components

**создание компонента**
```cmd
npm run c <название>
npm run c <название1> <название2>
```

**создание UI компонента**
```cmd
npm run ui <название>
npm run ii <название1> <название2>
```
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
```cmd
npm run p <название>
npm run p <название1> <название2>
```

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
```typescript
import name from "@/components/name"
import name from "@/page/name"
import name from "@/styles/name"
import name from "@/api/name"
...
```


работает автоимпорт

для упрощения работы с испортами абсолютных адресов, были записаны следющие правила:
```typescript
//vite.config.ts
...
resolve: {
	alias: [{ find: '@', replacement: path.resolve(__dirname, 'src') }]
}
```
```json
"baseUrl": ".",
"paths": {
	"@/*": ["./src/*"]
}
```
## Стили
### Sass
все стили стили должны быть модулями
```typescript
import s from "./name.module.scss"
```

класс корневого рордителя JSX елемента должен называться root
```tsx
<div className={s.root}> ...  </div>
```
```scss
//name.module.scss

.root{
	.element{}
	...
}
```

для работы с переменными подключается через дерективу `@use`. В `.scss` файл абсолютный импорт не работает.
```scss
//name.module.scss</i>
@use "../../styles/varable.scss" as v;

.root{
	background: <b>v.$bgColor</b>;
	...
}
```

### шрифты
Начертания шрифтов заранее заготовлены в виде классов. Название должны быть с сответствием дизайн проекта в Figma, только переписаны camelCase.
<pre><code><i>//Figma</i>
main_text * 16/20
</code></pre>
```tsx
//name.tsx

 < Element  className=<b>"mainText"</b> ...>
```
Используйте с библиотекой `clsx` для добавления класса или условия:
```tsx
//name.tsx
import cslx from 'clsx'

const [active,setActive] = useState<boolean>(false)
 < Element  className= {<b>clsx([s.root, "mainText", active && s.active</b>])} ...>
```

## Расширения для помощи
- [Figma for VS Code](https://marketplace.visualstudio.com/items?itemName=figma.figma-vscode-extension)
- [Git Graph](Git%20Graph)
- [Postman](https://marketplace.visualstudio.com/items?itemName=Postman.postman-for-vscode)
- [SCSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-scss)

