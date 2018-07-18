# Web micro-services in Go

## Task

Test how web micro-services can be written/developed in Go. 

Features to check

- [x] provide RESTful API for a fake "Todo" service
- [x] deploy service to Cloud Foundry
- [ ] provide WebSocket endpoint that reverses the string passed
- [ ] use RabbitMQ with publish/subscribe; implement something like _when I `POST` add aREST endpoint, inform via WebSocket through a RabbitMQ queue_
- [ ] check out `gorm` for ORM support
- [ ] use PostgreSQL as a database backend
- [ ] deploy micro-service and link it with RabbitMQ and MySQL services to Cloud Foundry: so we change the used database backend when deploying - how do we do it?
- [ ] use OAuth2 and authenticate and authorize against _Cloud Foundry's_ UAA    


## Components used

On my machine I used

- Windows `10.0.17134.137`
- Go `1.10.3 x64`
- cf CLI `cf version 6.36.2+18ceab10f.2018-05-16`
- PCF Dev `version 0.30.0 (CLI: 850ae45, OVA: 0.549.0)`
- GoLand as IDE


## Lessons learned

- how `GOPATH` works
- how `dep` works to store dependencies and resolve them to a `vendor` directory - needed to deploy external dependencies when staging in Cloud Foundry
- how the `manifest.yml` needs to written (`env` e.g. needs to contain `GOPACKAGENAME`, `command` contains the name of the binary to execute)
- Cloud Foundry buildpacks
    - how to use a remote buildpack in `cf push` with `-b https://....` 
    - how to update a buildpack with `cf update-buildpack` in a PCF Dev deployment
- `for i,v := range slice` returns the index `i` - for updating the element - and a copy `v` of the element - that can not be changed!  