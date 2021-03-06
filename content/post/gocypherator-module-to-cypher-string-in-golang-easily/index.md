---
title: "Gocypherator - Module to cypher string in Golang easily"
date: "2017-07-10"
categories: 
  - "golang"
  - "security"
tags: 
  - "cypher"
---

[Gocypherator](https://github.com/alknopfler/gocypherator) is a cypher module in order to encrypt / decrypt strings based on the following algorithms:

- AES-128,
- AES-192,
- or AES-256.

**Usage:**

First of all, you need to import the module:

```golang
import "github.com/alknopfler/gocypherator/cypher"
```

Then you have to initialize the cypher module with the type of algorithm:

```golang
func InitKeyCypher(cypherType int) {
```

`cypherType` could be:

- 16 ==> AES 128
- 24 ==> AES 192
- 32 ==> AES 256

The following example shows all the features available:

```golang
func main (){
    var cypherType = 16
    var baseText = "helloWorld"

    fmt.Println("Base Text: ",baseText)

    k:= cypher.InitKeyCypher(cypherType)

    crypt := k.EncryptString(baseText)
    fmt.Println("Text Encrypted: ", crypt)

    decrypt := k.DecryptString(crypt)
    fmt.Println("Text Decrypted: ",decrypt)

}
```
