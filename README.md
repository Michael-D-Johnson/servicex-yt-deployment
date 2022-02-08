Here is an example using the [ServiceX frontend](https://github.com/ssl-hep/ServiceX_frontend):

```
from servicex import ServiceXDataset
from servicex.servicex_python_function import ServiceXPythonFunction
from servicex import MinioAdaptor

def transform_yt(ds):
    slc = ds.r[ds.domain_center[0], :, :].plot(("gas", "density"))
    sac = slc.frb[("gas", "density")].d
    return sac

if __name__ == "__main__":
    dataset = "girder://579fb0aa7b6f0800011ea3b6#item"
    
    ds = ServiceXDataset(dataset, 
                         backend_name = "python",
                         minio_adaptor = MinioAdaptor('localhost:{your Minio port}))
    selection = ServiceXPythonFunction(ds)
    encoded_selection = selection._encode_function(transform_yt)
    r = ds.get_data_pandas_df(encoded_selection)
    print(r)
```
