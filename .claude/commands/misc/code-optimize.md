---
description: Analyze and optimize code for performance, memory, and efficiency
model: claude-sonnet-4-5
---

Optimize the following code for performance and efficiency.

## Code to Optimize

$ARGUMENTS

## Optimization Strategy

### 1. **Profiling First**
- Identify actual bottlenecks
- Don't optimize prematurely
- Measure before and after
- Focus on high-impact areas

### 2. **Performance Optimization Areas**

**Python (FastAPI/Flask)**
- Use async/await for I/O-bound operations
- Connection pooling for databases
- Use generators for large datasets
- Caching with Redis or in-memory
- Profile with cProfile, py-spy
- Use uvloop for async performance

**JavaScript/TypeScript (Node.js/Express/React)**
- Event loop optimization
- Cluster mode for CPU-bound tasks
- Memoization (useMemo, useCallback for React)
- Code splitting and lazy loading
- Stream large responses
- Use worker threads for heavy computation

**Go**
- Goroutine optimization
- Channel buffering strategies
- Memory pooling (sync.Pool)
- Reduce allocations
- Profile with pprof
- Use benchmarks (go test -bench)

**Rust**
- Avoid unnecessary clones
- Use references and borrowing efficiently
- Leverage zero-cost abstractions
- Profile with flamegraph/perf
- Use release builds with LTO

**Flutter/Dart**
- Widget rebuild optimization (const constructors)
- Lazy loading and pagination
- Image caching and optimization
- Avoid expensive operations in build()
- Use isolates for heavy computation

**Kotlin (Android/AR Core)**
- Avoid object allocations in loops
- Use sequences for lazy evaluation
- Coroutine optimization
- Memory leak prevention
- Profile with Android Profiler

**Database Queries (AWS RDS PostgreSQL)**
- Add indexes for frequently queried fields
- Use EXPLAIN ANALYZE
- Batch queries (reduce N+1 problems)
- Use SELECT with specific columns
- Implement pagination
- Connection pooling (PgBouncer)
- Optimize JOINs and subqueries

**API Calls**
- Implement caching strategies
- Debounce/throttle requests
- Parallel requests where possible
- Request deduplication
- Optimistic updates

### 3. **Optimization Checklist**

**General**
-  Use appropriate data structures (HashMap vs List)
-  Avoid nested loops where possible
-  Cache expensive computations
-  Minimize I/O operations
-  Batch database operations

**Memory**
-  Fix memory leaks
-  Use object pooling for frequent allocations
-  Stream large data instead of loading all
-  Clear references when done
-  Profile memory usage

**Concurrency**
-  Use async for I/O-bound tasks
-  Use threads/workers for CPU-bound tasks
-  Avoid lock contention
-  Use appropriate concurrency primitives

**Network**
-  Compress responses (gzip/brotli)
-  Use CDN for static assets
-  Minimize payload size
-  Implement proper caching headers
-  Use HTTP/2 or HTTP/3

### 4. **Measurement Tools**

**Python**: cProfile, py-spy, memory_profiler, line_profiler
**JavaScript/Node.js**: Chrome DevTools, clinic.js, 0x
**Go**: pprof, trace, benchstat
**Rust**: flamegraph, perf, criterion
**Flutter**: DevTools, Observatory
**Kotlin/Android**: Android Profiler, LeakCanary
**Database**: EXPLAIN ANALYZE, pg_stat_statements, AWS RDS Performance Insights

### 5. **Common Optimizations**

**Replace inefficient iterations**
```python
# Python - Before: Multiple iterations
result = sum(x * 2 for x in arr if x > 0)

# After: Single pass with filter and map
from itertools import filterfalse
result = sum(map(lambda x: x * 2, filter(lambda x: x > 0, arr)))
```

```go
// Go - Use pre-allocated slices
// Before
var result []int
for _, v := range data {
    result = append(result, v*2)
}

// After
result := make([]int, len(data))
for i, v := range data {
    result[i] = v * 2
}
```

**Database query optimization**
```sql
-- Before: N+1 query
SELECT * FROM users;
-- Then for each user: SELECT * FROM orders WHERE user_id = ?

-- After: Single JOIN
SELECT u.*, o.* FROM users u
LEFT JOIN orders o ON u.id = o.user_id;
```

## Output Format

1. **Analysis** - Identify performance bottlenecks
2. **Optimized Code** - Improved version
3. **Explanation** - What changed and why
4. **Benchmarks** - Expected performance improvement
5. **Trade-offs** - Any complexity added
6. **Next Steps** - Further optimization opportunities

Focus on practical, measurable optimizations that provide real value. Don't sacrifice readability for micro-optimizations.
