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

### API - Erste Schritte
Ich erstelle eine neues Verzeichnis `/home/tori/microservices/ServerAPI` und erstelle dort mit `nano serverapi.go` eine Datei mit folgendem Inhalt:
```
package main

import (
        "fmt"
        "log"
        "net/http"
)

func homePage(w http.ResponseWriter, r *http.Request) {
        fmt.Fprintf(w, "Welcome to the HomePage!")
        fmt.Println("Endpoint Hit: homePage")
}

func handleRequests() {
        http.HandleFunc("/", homePage)
        log.Fatal(http.ListenAndServe(":10000", nil))
}

func main() {
        handleRequests()
}
```
Übrigens kann mit `go fmt serverapi.go` diese Datei automatisch formatieren lassen.
```
go build serverapi.go
go run serverapi.go
```
Damit habe ich einen sehr einfachen Server erstellt, der HTTP-Anfragen verarbeiten kann.
Mein "Debian-Server", auf dem ich arbeite hat die IP: `192.168.95.127`. Da ich in der Funktion `handleRequests()` den Port "10000" bestimmt habe, kann ich so jetzt diese API aufrufen `http://192.168.95.127:10000/` und bekomme im Browser diese Antwort: "Welcome to the HomePage!"
