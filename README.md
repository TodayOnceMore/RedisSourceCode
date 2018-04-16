# RedisSourceCode
Redis3.0源码注解
```graphviz
digraph finite_state_machine {
    rankdir=LR;
    size="8,5"

    node [shape = doublecircle]; S;
    node [shape = point ]; qi

    node [shape = circle];
    qi -> S;
    S  -> q1 [ label = "a" ];
    S  -> S  [ label = "a" ];
    q1 -> S  [ label = "a" ];
    q1 -> q2 [ label = "ddb" ];
    q2 -> q1 [ label = "b" ];
    q2 -> q2 [ label = "b" ];
}
```

```go
func moveZeroes(nums []int)  {
	zeroCount, numLen := 0, len(nums)
	for i := 0; i < numLen; i++ {
		if nums[i] == 0 {
			zeroCount++
		} else {
			if zeroCount > 0 {
				nums[i - zeroCount] = nums[i]
			}
		}
	}

	for i := numLen - zeroCount; i < numLen; i++ {
		nums[i] = 0
	}
	fmt.Println(nums)
}
```
