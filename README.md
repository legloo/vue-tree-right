# vue-tree-right

# Usage
```js
1.import TreeRight from "vue-tree-right"
2.components: {
    TreeRight,
  }
3.list: [//datasource
        {
          id: "z1",
          name: "leglo",
          age: "18",
          gender: "男",
          work: "web",
          children: [
            {
              name: "leglo1",
              age: "18",
              gender: "男",
              work: "web",
              id: "z1-1",
              children: [
                {
                  name: "leglo1-1",
                  age: "18",
                  gender: "男",
                  work: "web",
                  id: "z1-1-1",
                  children: [
                    {
                      name: "leglo1-1-1",
                      age: "18",
                      gender: "男",
                      work: "web",
                      id: "z1-1-1",
                    },
                  ],
                },
                {
                  id: "z1-1-2",
                  name: "leglo1-2",
                  age: "18",
                  gender: "男",
                  work: "web",
                },
                {
                  id: "z1-1-3",
                  name: "leglo1-3",
                  age: "18",
                  gender: "男",
                  work: "web",
                },
                {
                  id: "z1-1-4",
                  name: "leglo1-4",
                  age: "18",
                  gender: "男",
                  work: "web",
                },
              ],
            },
            {
              name: "leglo2",
              id: "z1-2",
              age: "18",
              gender: "男",
              work: "web",
            },
          ],
        },
      ],
      showFields: [//show fields
        {
          name: "姓名：",
          key: "name",
        },
        {
          name: "年龄：",
          key: "age",
        },
      ],
      
4.    <TreeRight :list="list" :showfields="showFields" />

```

# Preview
![image](https://github.com/zhuyuhaoliar/vue-tree-right/blob/master/20200826150513.jpg?raw=true)

# notice
## Id is a must. It can be any string that does not repeat;
## if showFields have no length,you will see nothing in box *_*;
## vue-tree-down will coming soon ~~~~~~~;