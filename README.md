This was tested on a Macbook using [minikube](https://minikube.sigs.k8s.io/docs/start/). The ServiceX yaml is a modified from the [ServiceX](https://github.com/ssl-hep/ServiceX/tree/develop/servicex) repository.

## Step 1: Install minikube
```
brew install minikube
```

## Step 2: Start minikube
```
minikube start
```

## Step 3: Install ServiceX
```
helm install servicex servicex/
```

## Step 4: Test Girder DID Finder -> Python Code Gen -> yt transformer 

### Using json file and post to 
```
cd tests
python3 post.py <servicex port> yt.item.json
```

### Here is an example using the [ServiceX frontend](https://github.com/ssl-hep/ServiceX_frontend):

```
cd tests
python3 frontend_tests.py <minio_host:minio_port>
```
