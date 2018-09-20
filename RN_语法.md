###生成数组或者list
```
let rowData = Array.from({length: 2}, (value, index) => {
            return `item -> ${index}${value}`;
        });
```
###遍历数组或者list
```
 rowData.map((value, index)=>{
            s+=value;
        })
```