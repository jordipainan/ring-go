# ring-go
implementation of linkable ring signatures using elliptic curve crypto in go

### requirements
go ^1.10

### get
`go get github.com/noot/ring-go`

### usage	
the branch `unique` is an implementation of unique ring signatures (no key images). the branch `linkable` contains an implementation of linkable ring signatures.

the algorithm including `Sign()` and `Verify()` (and Link() for linkable) is located in `ring/ring.go`.

to use the cli, perform the following:
```
cd $GOPATH/github.com/noot/ring-go
go build && go install
ring-go [flags] [opts]
```

cli flags:

`ring-go --gen` generate a new public-private key pair and save the files in the ./keystore directory.

`ring-go --sign /path/to/pubkey/dir /path/to/privkey.priv message.txt` sign a message inside `message.txt` using the private key at `privkey.priv` and the public keys inside the specified folder. note: inside `/path/to/pubkey/dir`you can only have pubkeys in their 64-byte format as generated by this cli. this will generate an output signature file and save it in the ./signatures directory.

`ring-go --verify /path/to/signature.sig` verify a signature file generated by this program.

### future
* integrate cli with mixer contract

### references
this implementation is based off of Ring Confidential Transactions. https://eprint.iacr.org/2015/1098.pdf
