[![GoDoc](https://godoc.org/github.com/lucasmenendez/gotagger?status.svg)](https://godoc.org/github.com/lucasmenendez/gotagger)
[![Build Status](https://travis-ci.org/lucasmenendez/gotagger.svg?branch=master)](https://travis-ci.org/lucasmenendez/gotagger)
[![Report](https://goreportcard.com/badge/github.com/lucasmenendez/gotagger)](https://goreportcard.com/report/github.com/lucasmenendez/gotagger)

# Gotagger
Simple keyword extraction

## Installation
```bash
go install github.com/lucasmenendez/gotagger
```

### Stopwords
If you want to extend stopword list, create a file, named as language code, into a any folder (for example: `en` file will contain English stopwords). Then, set env var `STOPWORDS` to that folder path.
Extended stopword lists can be found in [Stopwords ISO profile](https://github.com/stopwords-iso).

## Demo
```go
package main

import (
    "fmt"
    "github.com/lucasmenendez/gotokenizer"
    "github.com/lucasmenendez/gotagger"
)

func main() {
    var limit int = 15
    var lang string = "<input-lang>"
    var text string = "<input-text>"
    
    var words [][]string
    for _, s := range gotokenizer.Sentences(text) {
        words = append(words, gotokenizer.Words(s))
    }
    
    if tags, err := gotagger.GetTags(words, lang, limit); err != nil {
        fmt.Println(err)
    } else {
        fmt.Printf("%q\n", tags)
    }
}
```