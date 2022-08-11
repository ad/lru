# LRU Cache

A simple LRU cache using go generics.

It automatically removes elements as new elements are added if the capacity is reached. Items are removes based on how recently they were used where the oldest items are removed first.

## CONSTANTS

```go
const (
        // DefaultCacity is the default cache capacity
        DefaultCapacity = 10000
)
```

## TYPES

```go
type Cache[K comparable, V any] struct {}
```

## FUNCTIONS

New initializes a new lru cache with the given capacity.

```go
func New[K comparable, V any](cacheOptions ...CacheOption) *Cache[K, V]
```

Delete an item from the cache.

```go
func (c *Cache[K, V]) Delete(key K) bool
```

Flush deletes all items from the cache.

```go
func (c *Cache[K, V]) Flush()
```

Get an item from the cache. This operation updates recent usage of the item.

```go
func (c *Cache[K, V]) Get(key K) (value V, ok bool)
```

Keys returns a slice of all the keys in the cache.

```go
func (c *Cache[K, V]) Keys() []K
```

Len is the number of key value pairs in the cache.

```go
func (c *Cache[K, V]) Len() int
```

Peek gets an item from the cache without updating the recent usage.

```go
func (c *Cache[K, V]) Peek(key K) (value V, ok bool)
```

Set the given key value pair. This operation updates the recent usage of the item.

```go
func (c *Cache[K, V]) Set(key K, value V)
```

### CacheOption configurs a lru cache.

```go
type CacheOption interface {}
```

WithCapacity configures how many items can be stored before old items begin to be deleted.

```go
func WithCapacity(capacity int) CacheOption
```
