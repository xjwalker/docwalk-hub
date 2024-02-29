# Golang docker image

## Steps for running golang without installing it in your system
1. Install docker
2. Run 
`docker pull golang`
3. Run the image with the following command:
 ```
docker run --rm --name my-golang -v /Users/jwalker4/Documents/code/docwalk-hub/go:/go/src/my-golang -w /go/src/my-golang golang:latest go run hello.go
```

### keynotes on command:
- `--rm` - remove the container after it stops
- `--name` - name the container
- `-v` - mount the local directory to the container
- `-w` - set the working directory in the container
- `golang:latest` - the image to run
- `go run hello.go` - the command to run in the container
