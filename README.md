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
und hier der Quellcode:
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
# Ausgabe: Hello World
```
### Der Go-Workspace / Go-Module
Nach der Installation mit `apt install golang` wurde bei mir im Verzeichnis `/usr/lib/go` der "Go-Workspace" mit z.B. den Ordnern `/bin` und `/source` angelegt. Dieses Verzeichnis kann, muss aber nicht genutzt werden, seitdem 2018 die Go-Module eingeführt wurden.
```
# Einrichten eines Go-Modul-Projekts, z.B.:
cd /home/tori/microservices
go mod init github.com/richtertoralf/Microservices_Go
```
Dabei wird die Datei (Manifestdatei) `go.mod` angelegt, in der vorallem Abhängikeiten verwaltet werden können.
