
<table width="100%">
<tr>
    <th>
        
    ```diff
+ this text is highlighted in green
- this text is highlighted in red
```
        
    </th>
    <th>Don't</th>
  </tr>
<tr>
<td>

  ```kotlin
  if(condtion) {
    doSomething()
  } else {
    doSomethingElse()
  }
  ```

</td>
<td>

  ```kotlin
  when(condtion) {
    true -> doSomething()
    false -> doSomethingElse()
  }
  ```

</td>
</tr>
</table>

**Avoid nested ifs**

Following logic in a deeply nested if else mess can be hard and error prone for the next developer. There are several ways of avoiding that.

Consider inverting the expression and returning:
```kotlin
// Hard to follow
if (item != null) {
   if (item.getFollowers() != null && item.getFollowers().get(someId) != null) {
       follower = item.getFollowers().get(someId)
   }
}

// Better
if(item == null) {
    return
}

if(item.getFollowers() == null || !item.getFollowers().contains(someId)) {
    return
}

follower = item.getFollowers().get(someId)
```
