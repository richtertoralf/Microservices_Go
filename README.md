# Microservices_Go
Microservices mit Golang austesten
>Auf meinem Windows11 Pro Computer habe ich dazu eine **Debian 12 bookworm** Maschine in VirtualBox installiert.
### Installation
```
# Installation:
su
apt install golang
apt install git
# Testen der Installation / Version anzeigen:
go version
# go version go1.19.8 linux/amd64
```
### Hello World
```
mkdir microservices
cd microservices
git clone https://go.googlesource.com/example
cd example/hello/
go run hello.go
# Hello, Go examples!
```
und jetzt ein eigenes erstes Go-Programm
```
mkdir HelloWorld
cd HelloWorld
nano main.go
```
```
package main
import "fmt"
func main() {
    fmt.Println("Hello World")
}
```
```
go build main.go
go run main.go
# Hello World
```
