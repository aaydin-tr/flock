# flock
[![TravisCI Build Status](https://img.shields.io/travis/gofrs/flock/master.svg?style=flat)](https://travis-ci.org/gofrs/flock)
[![GoDoc](https://img.shields.io/badge/godoc-flock-blue.svg?style=flat)](https://godoc.org/github.com/aaydin-tr/flock)
[![License](https://img.shields.io/badge/license-BSD_3--Clause-brightgreen.svg?style=flat)](https://github.com/aaydin-tr/flock/blob/master/LICENSE)
[![Go Report Card](https://goreportcard.com/badge/github.com/aaydin-tr/flock)](https://goreportcard.com/report/github.com/aaydin-tr/flock)

`flock` implements a thread-safe sync.Locker interface for file locking. It also
includes a non-blocking TryLock() function to allow locking without blocking execution.

## License
`flock` is released under the BSD 3-Clause License. See the `LICENSE` file for more details.

## Go Compatibility
This package makes use of the `context` package that was introduced in Go 1.7. As such, this
package has an implicit dependency on Go 1.7+.

## Installation
```
go get -u github.com/aaydin-tr/flock
```

## Usage
```Go
import "github.com/aaydin-tr/flock"

fileLock := flock.New("/var/lock/go-lock.lock")

locked, err := fileLock.TryLock()

if err != nil {
	// handle locking error
}

if locked {
	// do work
	fileLock.Unlock()
}
```

For more detailed usage information take a look at the package API docs on
[GoDoc](https://godoc.org/github.com/aaydin-tr/flock).
