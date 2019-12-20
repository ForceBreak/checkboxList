# vue-basse

Компонент принимает на вход массив и число.
Массив используется для формирования списка checkbox`ов.
Число используется как ограничитель максимального количества выбранных элементов.
При каждом действии (выбор/снятие выбора) происходит emit события, в котором передаётся массив выбраннх элементов.

## Минимальный набор для элемента массива
{ id, name }

# Добавлен пример работы с атрибутом IS
Динамическа подгрузка компонентов по клику. Подгрузка идёт по параметру name внутри компонентов. Props передаются через v-bind, в котором указано computed свойство. События просто вешать на обёртку component.
#### !!! Важно:
имена прослушиваемых событий лучше все делать разными, чтобы избежать конфликтов при использовании, например, watch.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
