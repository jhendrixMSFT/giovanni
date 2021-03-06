## File Storage Files SDK for API version 2017-07-29

This package allows you to interact with the Files File Storage API

### Supported Authorizers

* SharedKeyLite (Blob, File & Queue)

### Example Usage

```go
package main

import (
	"context"
	"fmt"
	"time"
	
	"github.com/Azure/go-autorest/autorest"
	"github.com/tombuildsstuff/giovanni/storage/2017-07-29/file/files"
)

func Example() error {
	accountName := "storageaccount1"
    storageAccountKey := "ABC123...."
    shareName := "myshare"
    directoryName := "myfiles"
    fileName := "example.txt"
    
    storageAuth := autorest.NewSharedKeyLiteAuthorizer(accountName, storageAccountKey)
    filesClient := files.New()
    filesClient.Client.Authorizer = storageAuth
    
    ctx := context.TODO()
    input := files.CreateInput{}
    if _, err := filesClient.Create(ctx, accountName, shareName, directoryName, fileName, input); err != nil {
        return fmt.Errorf("Error creating File: %s", err)
    }
    
    return nil 
}
```