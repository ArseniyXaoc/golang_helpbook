# Slice
## Base functions
### Create 
`s := make([]int, 4, 7) // [0 0 0 0], len = 4 cap = 7`
### Copy
`copy(dest, src)`
### Append
`s := make([]int, 4, 7)`
`slice1 := append(s[:2], 2, 3, 4)`
`slice2 := append(s[1:2], 7)`
`slice3 := append(s, slice1[1:]...)`
### Sort
```
 s := []int{5, 4, 1, 3, 2}
    sort.Ints(s)
    fmt.Println(s) // [1 2 3 4 5] 
```
## Lifehacks:
### Удаление последнего элемента слайса:
```
s := []int{1, 2, 3}
if len(s) != 0 { // защищаемся от паники
    s = s[:len(s)-1]
}
fmt.Println(s) // [1 2]
```
### Удаление первого элемента слайса:
```
s := []int{1,2,3}
if len(s) != 0 { // защищаемся от паники
    s = s[1:]
} 
fmt.Println(s) // [2 3] 
```
### Удаление элемента слайса с индексом i:
```
s := []int{1,2,3,4,5}
i := 2

if len(s) != 0 && i < len(s) { // защищаемся от паники
    s = append(s[:i], s[i+1:]...)
} 
fmt.Println(s) // [1 2 4 5]
```
### Сравнение двух слайсов:
```
s1 := []int{1,2,3}
s2 := []int{1,2,4}
s3 := []string{"1","2","3"}
s4 := []int{1,2,3}

fmt.Println(reflect.DeepEqual(s1,s2)) // false
fmt.Println(reflect.DeepEqual(s1,s3)) // false
fmt.Println(reflect.DeepEqual(s1,s4)) // true
```