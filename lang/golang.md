# Golang: Quick Reference Card

## Imports

### Github

```go
import (
	"encoding/json"
	"fmt"
	"io/ioutil"
	"os"
	"sort"

    "github.com/r351574nc3/goproj/package/"
)
```

## Constants

```go
const (
	CONSTANT_NAME = "CONSTANT_VALUE"
)

var (
	// Store = new(store.Builder).WithRegistry().Build()
	Store = store.Setup(assign.New(), state.New())
)

```



## Types

### Arrays

```go
retval := new(SearchableDurationIndex)
retval.Items = make([]StateEventSummary, 0)

var a [5]int
fmt.Println("emp:", a)	

// inline
b := [5]int{1, 2, 3, 4, 5}
fmt.Println("dcl:", b)

// slice
c := make([]string, len(s))
copy(c, s)
l = [5]int{1, 2, 3, 4, 5}
l[0]                                  // single position
L[0:3]                                // the first three elements
L[-2:]                                // the last two elements
L[1:4] = [7,8]                        // substitute

append(L, x)
delete(L, 0)
```

### Maps
```go
m := make(map[string]int)
m["k1"] = 7
m["k2"] = 13
fmt.Println("map:", m)

delete(m, "k2")
fmt.Println("map:", m)

_, prs := m["k2"]
fmt.Println("prs:", prs)
```

### String Manipulation

```go
// copy string
c := make([]string, len(s))
copy(c, s)
```

### Regex


### Type Assertions


```go
func (s *EventSubscriptions) Publish(el *list.Element) {
	if subscriber.Match(el.Value.(types.Event)) {
	}
}

// declare interface and assign
var i interface{} = "a string"
 
//type-assertion
valueOfI := i.(string)    // "a string"
```

## JSON

## Functions

### Multiple return values

```go
func example() (int, int) {
	return 0, 0
}
```

### As Parameters
```go
	summaries, ok := store.DurationIndex.Filter(func(e types.StateEventSummary) bool {
		if state != "" && team != "" {
			return e.Status == state && e.Team == team
		}

		if state != "" {
			return e.Status == state
		}

		if team != "" {
			return e.Team == team
		}

		return true
	})
```

## Loops

```go
for j := 7; j <= 9; j++ {
	fmt.Println(j)
}

// while loop
i := 1
for i <= 3 {
	fmt.Println(i)
	i = i + 1
}

// Infinite loops
for {
	fmt.Println("loop")
	break
}

// foreach for arrays
nums := []int{2, 3, 4}
sum := 0
for _, num := range nums {
	sum += num
}
fmt.Println("sum:", sum)

for i, num := range nums {
	if num == 3 {
		fmt.Println("index:", i)
	}
}

// foreach for maps
kvs := map[string]string{"a": "apple", "b": "banana"}
for k, v := range kvs {
	fmt.Printf("%s -> %s\n", k, v)
}
```

## Structs

```go
// JSON Struct
type Event struct {
	Id        int         `form:"case_id" json:"case_id" binding:"required"`
	Timestamp time.Time   `form:"timestamp" json:"timestamp" binding:"required"`
	Assignee  string      `form:"assignee" json:"assignee" binding:"required"`
	Team      string      `form:"team" json:"team" binding:"required"`
	State     *Transition `form:"state" json:"state" binding:"required"`
}
```

## Interfaces

```go
type CoolInterface interface {
	CoolMethod1(CoolParameter)
	CoolMethod2(*list.Element)
	CoolMethod3(CoolParameter2) bool
}
```

## Object-oriented 

```go
new(AssignmentSubscriber)          // Instantiate class

```

```go
package assign

import (
	"github.com/r351574nc3/project/events/types"
)

// Creates assign.New()
func New() types.Subscriber {
	return new(AssignmentSubscriber).Init()
}
```

### Methods

```go
var (
	store         *EventStore
)
```

Go doesn't have constructors. This allows us to create a `store.New()`
```go
func (s *EventStore) New() *EventStore {
	if s == nil {
		return new(EventStore).Init()
	}
	return s
}
```

## Errors and Exceptions

## System

## Concurrency

## REST Api

```go
package main

import (
	"github.com/gin-gonic/gin"
)

func createRouter() *gin.Engine {
	r := gin.Default()

	// Get total hours for cases value
	r.POST("/cases", func(c *gin.Context) {
		c.JSON(200, response)
	})
	return r
}

func main() {
	r := createRouter()

	r.Run(":8080")
}

```

## REST Client