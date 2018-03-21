# wercker goveralls step

[![wercker status](https://app.wercker.com/status/0c4ad38afcbe5edff73cf590f7131e59/m "wercker status")](https://app.wercker.com/project/bykey/0c4ad38afcbe5edff73cf590f7131e59)

This [wercker](http://wercker.com) step runs [goveralls](https://github.com/mattn/goveralls)
to extract code coverage from your project and uploads it to [Coveralls](https://coveralls.io/).

It also exclude the "vendor" directory from the "tests" scanned directories.

It also include only tests files that have the "unit" tag.

## Usage

```yaml
box: google/golang
build:
  steps:
    - setup-go-workspace
    - golint
    - script:
        name: go build
        code: |
          go build ./...
    - script:
        name: go test
        code: |
          go test ./...
    - ricardo-ch/goveralls:
        token: $COVERALLS_TOKEN
```

## Properties

Name     | Type   | Default                 | Description
-------- | ------ | ----------------------- | -------------------
token    | string |                         | Your Coveralls repository token.

## Changelog

### 1.1.1

- Allow go version retrieval for go1.10

### 1.0.0

- Exclude "vendor" folder from scanned directories
- Filter test files that have "unit" tag
- Fork repo