# Notebook 8.5 problems

## 2/5 update
1. Cannot have several TF2 estimators existing simultaneously. So currently only the `gan` model is written as a TF2 esitmtor.

2. Error occurs when constructing model

    ```py
    gan_est = Estimator.from_keras(model_creator=gan_creator)
    ```

    Error message in notebook is not complete. Full error message is shown here:

    ```py
    Traceback (most recent call last):
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/serialization.py", line 378, in serialize
        raise e
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/serialization.py", line 375, in serialize
        value, protocol=5, buffer_callback=writer.buffer_callback)
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/cloudpickle/cloudpickle_fast.py", line 72, in dumps
        cp.dump(obj)
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/cloudpickle/cloudpickle_fast.py", line 617, in dump
        return Pickler.dump(self, obj)
    TypeError: can't pickle _thread.RLock objects
    Exception ignored in: 'ray._raylet.prepare_args'
    Traceback (most recent call last):
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/serialization.py", line 378, in serialize
        raise e
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/serialization.py", line 375, in serialize
        value, protocol=5, buffer_callback=writer.buffer_callback)
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/cloudpickle/cloudpickle_fast.py", line 72, in dumps
        cp.dump(obj)
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/cloudpickle/cloudpickle_fast.py", line 617, in dump
        return Pickler.dump(self, obj)
    TypeError: can't pickle _thread.RLock objects
    Traceback (most recent call last):
    File "test.py", line 102, in <module>
        gan_est = Estimator.from_keras(model_creator=gan_creator)
    File "/home/jinglei/analytics-zoo/pyzoo/zoo/orca/learn/tf2/estimator.py", line 45, in from_keras
        backend=backend, compile_args_creator=compile_args_creator)
    File "/home/jinglei/analytics-zoo/pyzoo/zoo/orca/learn/tf2/estimator.py", line 137, in __init__
        [worker.get_node_ip.remote() for worker in self.remote_workers])
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/worker.py", line 1513, in get
        raise value.as_instanceof_cause()
    ray.exceptions.RayTaskError(AssertionError): ray::IDLE (pid=7134, ip=10.239.44.107)
    File "python/ray/_raylet.pyx", line 414, in ray._raylet.execute_task
    File "python/ray/_raylet.pyx", line 417, in ray._raylet.execute_task
    File "python/ray/_raylet.pyx", line 440, in ray._raylet.execute_task
    File "/home/jinglei/anaconda3/envs/tf2/lib/python3.7/site-packages/ray/signature.py", line 139, in recover_args
        "Flattened arguments need to be even-numbered. See `flatten_args`.")
    AssertionError: Flattened arguments need to be even-numbered. See `flatten_args`.
        
    ```