Elkészült production kód futtatásához szükséges függőségek kérdése

"works on my machine"

független, hordozható deployment unit

## Szerver virtualizáció

"Server virtualization is a software architecture that allows more than one server operating system to run as a guest on a given physical server host. With the server software abstracted away from the physical machine in this way, the server becomes a "virtual machine," detached from the physical plane—though the server "thinks" it is running exclusively on the compute and memory resources. It’s actually running on a virtual imitation of the server hardware." 

"Server virtualization enables more efficient use of IT resources than was previously possible. Before server virtualization, it was common to have under- and over-utilized hardware in the same data center. With virtualization, one can move workloads between virtual machines according to load. The same physical server can also run multiple server operating systems and configurations, further increasing efficiency. Server virtualization is the basis for cloud computing and hybrid IT."

(https://www.hpe.com/us/en/what-is/server-virtualization.html)


Néhány példa
+ VMVare
+ VirtualBox
+ HyperV


## Docker

A VMek futtatása drága

Linux namespace-ek, konténer technológia, ugyanaz az operációs rendszer

Docker vs Server virtualization

Image vs container

### Docker gyakorlatok

#### docker run

`docker run -it --rm alpine sh `
 ( + 2 container állapot )

`docker container ls`

`docker image ls`

`docker run --rm -i -t nacyot/fortran-gfortran:apt sh`  
(https://github.com/nacyot/docker-programming-languages/blob/master/fortran-gfortran-apt/hello_world.f)

`docker run --rm -i -t -v $(pwd):/source nacyot/fortran-gfortran:apt gfortran -o hello_world /source/hello_world.f`

`docker pull` és `docker push` (docker hub)

`docker pull mcr.microsoft.com/dotnet/sdk:6.0`

`docker run -it mcr.microsoft.com/dotnet/sdk:6.0 bash`

`docker exec <container_id> dotnet run --project /root/app/app.csproj`

### Dockerfile

Konténerizáljuk az api-t

`docker build -f .\dockerfile -t food_api .\Egyetem_api_beadando_2021\api`

`docker run -p 8400:8000 -d food_api`

`docker logs -f <container_id>`

A teszteket is

`docker build -f .\Dockerfile.tests -t drink_test_api .\Egyetem_api_beadando_2021\drink_test\`

` docker run -it --network=container:<container_id> drink_test_api`

