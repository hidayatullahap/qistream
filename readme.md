# QiStream

simple package stream in qasir tech

## Instalation

```
# Go modules
$> go mod tidy
```

## Basic Usage
 
Env
```
convert file credential.json to base64 --> https://www.base64decode.org/
GCP_CREDENTIALS=someCodeBas64
GCP_PROJECT_ID=ProjectId
PUBSUB_TOPIC=TopicName
PUBSUB_SUBSCRIPTION_ID=SubcriptionName
```

Sample
```
import (
	"log"
	"github.com/jinzhu/gorm"
	"github.com/qasir-id/qistream/service/pubsub"
)
    //for async
	log.Println("starting Pub/Sub Client ")
	// RUN service PubSub
	var db *gorm.DB
	psService := pubsub.NewPubSubService(db, pubsub.NewClient())
	if err := psService.AsyncPull(func() {
		//put code process subcribe
	}); err != nil {
		log.Fatalf("failed to pull pub/sub message : %v", err)
	}

    //for publish
    ctx := context.Background()
	var pubMessage []byte
	pubsub.PublishTopic(ctx, pubMessage, "TOPIC_NAME")
    
    //you can also see in example folder
```