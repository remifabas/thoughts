# PPROF

[pprof](https://github.com/google/pprof)
pprof is a tool for visualization and analysis of profiling data.

## Analyse web server

Add this to you program

```go
package main

import _ "net/http/pprof"
import "net/http"

func main() {
    go func() {
        _ = http.ListenAndServe("localhost:6060", nil)
    }()
    // your code
}

```

Then you can make an http call to localhost:6060

### RAM profiling

A little info:
In order to analyze the currently used memory, just select the inuse indices (bytes or object counts):

- inuse_space: memory allocated but not yet released
- inuse_objects: objects allocated but not yet released

If you are interested in understanding the total amount of bytes or objects, use the alloc indices instead:

- alloc_space:   the  total amount of memory allocated
- alloc_objects : the  total number of objects allocated

flat: the memory allocated and held by this function
cum: the memory allocated by this function together with functions that it has called

Ok let's get some info !
Retrieve inuse_space: (by default --inuse_space you can forget it)

```bash
go tool pprof --inuse_space -top http://localhost:6060/debug/pprof/heap
go tool pprof -png http://localhost:6060/debug/pprof/heap > ram.png
```

Retrieve alloc_space

```bash
go tool pprof --alloc_space -top http://localhost:6060/debug/pprof/heap
```

### CPU profiling

```bash
go tool pprof -png "http://localhost:6060/debug/pprof/profile?seconds=5" >cpu.png
```

## In test

https://wablesushmita.medium.com/cpu-memory-profiling-with-golang-pprof-3deddbd7b964

```bash
go test -cpuprofile cpu.prof -memprofile mem.prof
go tool pprof cpu.prof
go tool pprof cpu.prof

go-torch generate svg
```
