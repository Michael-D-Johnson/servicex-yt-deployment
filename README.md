This was tested on a Macbook using [minikube](https://minikube.sigs.k8s.io/docs/start/). The ServiceX yaml is a modified from the [ServiceX](https://github.com/ssl-hep/ServiceX/tree/develop/servicex) repository.

## Step 1: Install minikube

See minikube documentation on installation instructions for your particular machine.

## Step 2: Start minikube
```
minikube start
```

## Step 3: Install ServiceX
### a) Update the adminEmail in servicex/values.yaml file.

### b) Update helm dependencies
```
cd servicex
helm dependency update
```

### c) Install ServiceX
```
helm install servicex servicex/
```

## Step 4: Test Girder DID Finder -> Python Code Gen -> yt transformer 

### Using json file and post to ServiceX /transformation endpoint
```
cd tests
python3 post.py <servicex_port> yt.item.json
```

### Here is an example using the [ServiceX frontend](https://github.com/ssl-hep/ServiceX_frontend):
#### a) update ServiceX host in the api_endpoints section of tests/ServiceX_frontend/config_default.yaml
#### b) run frontend_test.py code
```
cd tests/ServiceX_frontend
python3 frontend_test.py <minio_host:minio_port>
```


## Considerations

### Minio settings
This setup doesn't use a persistent volume and requests 1Gi in memory. You may need to change that.
