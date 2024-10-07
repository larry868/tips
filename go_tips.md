# Go Tips

https://go.dev/

## FUSE (Frequent Use)

- [Language Specification](https://go.dev/ref/spec) (go.dev)
- [String Formating](https://pkg.go.dev/fmt) (pkg.go.dev/fmt)
- [Date & Time Formating](https://pkg.go.dev/time#pkg-constants)
- [Array vs Slice vs Map](http://donofden.com/blog/2019/09/20/golang-array-slice-map)
- [Closures and anonymous](https://www.bogotobogo.com/GoLang/GoLang_Closures_Anonymous_Functions.php)
- [Implementing Enums in Golang](https://levelup.gitconnected.com/implementing-enums-in-golang-9537c433d6e2)
- clear a map
    ```go
    for k := range m {
        delete(m, k)
    }
    ```
- [Writing a Go client for your RESTful API](https://medium.com/@marcus.olsson/writing-a-go-client-for-your-restful-api-c193a2f4998c)
- [BogoToBogo](https://www.bogotobogo.com/GoLang/GoLang_HelloWorld.php) (GoLang Tutorial)
- [Go By Example](https://gobyexample.com/)

## Program Struture

- [Initiation aux modules](https://dpp.st/blog/golang-modules/)
- [Everything you need to know about Packages in Go](https://medium.com/rungo/everything-you-need-to-know-about-packages-in-go-b8bac62b74cc)
- [Executable and non-executable module in Go (Golang)](https://golangbyexample.com/type-module-golang/) golangbyexample.com

## Build & Deploy

- [how to deploy step by step](https://codesahara.com/blog/how-to-deploy-golang-to-production-step-by-step/)

```bash
# build for another platform eg Raspi
GOOS=linux GOARCH=arm GOARM=5 go build;

# runing full tests
go test ./...
```

## Publishing

- [Publishing a module](https://go.dev/doc/modules/publishing) (go.dev)


```bash
# first of all you need to commit and pull everything
git checkout master
git fetch origin master
git add .
git commit -m "publish v{x.y.z}"
git push origin 

# create a git tag for the version to deploy
# the version number must start with a lowercase `v`
# major version number are significant (v0... and v1... are considered differently)
git tag v{x.y.z}

# push the tag, because they're not pushed with your commits
git push origin v{x.y.z}
# or 
git push --tags

# Then list your sources under golang.org
GOPROXY=proxy.golang.org go list -m github.com/{gituser}/{repo}@v{x.y.z}
```

