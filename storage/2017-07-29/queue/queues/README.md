## Queue Storage Queues SDK for API version 2017-07-29

This package allows you to interact with the Queues Queue Storage API

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
	"github.com/tombuildsstuff/giovanni/storage/2017-07-29/queue/queues"
)

func Example() error {
	accountName := "storageaccount1"
    storageAccountKey := "ABC123...."
    queueName := "myqueue"
    
    storageAuth := autorest.NewSharedKeyLiteAuthorizer(accountName, storageAccountKey)
    queuesClient := queues.New()
    queuesClient.Client.Authorizer = storageAuth
    
    ctx := context.TODO()
    metadata := map[string]string{
    	"hello": "world",
    }
    if _, err := queuesClient.Create(ctx, accountName, queueName, metadata); err != nil {
        return fmt.Errorf("Error creating Queue: %s", err)
    }
    
    return nil 
}
```