# testquest

## Использование

1. Установить `npm i testquest`
2. Импортировать стили `import testquest/dist/index.css`
3. Установить шрифт Roboto Ligth, например
```
<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap" rel="stylesheet">
```
4. Установить font awesome free.
5. Использовать компонент в нужном месте:
```
<template>
  <div>
    <TargetComponent :list="list" :change-list="changeList" :check-item="changeChecked" />
  </div>
</template>

<script>
import TargetComponent from 'testquest';

export default {
  components: {
    TargetComponent,
  },
  data(){
    return {
      list: [
        {id: '1', text: 'Line 1'},
        {id: '2', text: 'Line 1'},
        {id: '3', text: 'Line 1'},
        {id: '4', text: 'Line 1'},
        {id: '5', text: 'Line 1'},
        {id: '6', text: 'Line 1'},
        {id: '7', text: 'Line 1'},
        {id: '8', text: 'Line 1'},
        {id: '9', text: 'Line 1'},
        {id: '10', text: 'Line 1'},
        {id: '11', text: 'Line 1'},
        {id: '12', text: 'Line 1'},
        {id: '13', text: 'Line 1'},
        {id: '14', text: 'Line 1'},
      ],
      checked: [],
    };
  },
  methods: {
    changeList(data) {
      this.list = [...data];
    },
    changeChecked(data) {
      this.checked = [...data];
    },
  },
}
</script>
``` 
