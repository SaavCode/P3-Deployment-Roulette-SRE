# Step 5: Observability with metrics

1. I installed a metric server using `kubectl apply -f metrics-server.yml`  to improve overall observability.

2. I used `kubectl top pods` to find the pods with most usage: 

    ```
nestorsaavedra 🦊 bloatware >> kubectl top pods --sort-by=memory
NAME                                  CPU(cores)   MEMORY(bytes)   
hello-world-bd9cf44f8-tspfq           2m           20Mi              
    ```

3. From the output, I found that the `hello-world-bd9cf44f8-tspfq ` pod had the most memory usage and was at (20Mi).

4. To fix this, I deleted the `hello-world-bd9cf44f8-tspfq ` pod:

    ```
nestorsaavedra 🦊 bloatware >> kubectl delete pod hello-world-bd9cf44f8-tspfq 
pod "hello-world-bd9cf44f8-tspfq" deleted
    ```

5. Lastly to confirm that memory usage had not increased I ran `kubectl top pods`:

    ```
nestorsaavedra 🦊 bloatware >> kubectl top pods --sort-by=memory
NAME                                  CPU(cores)   MEMORY(bytes)   
green-6dbbc7db7c-v9h69                1m           2Mi             
blue-756d6cc6c9-9b79w                 1m           2Mi             
green-6dbbc7db7c-8jtrh                1m           2Mi             
green-6dbbc7db7c-r6w2l                1m           2Mi             
blue-756d6cc6c9-n2bpc                 1m           2Mi             
blue-756d6cc6c9-wdw5z                 1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-wwmjm   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-ql7xl   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-zvpz7   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-zghbh   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-nkkcg   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-th8bv   1m           2Mi             
canary-v2-6bdbfc4f4b-254gp            0m           2Mi             
bloaty-mcbloatface-7d7b64c65d-vrpbh   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-lv8kg   1m           2Mi             
canary-v2-6bdbfc4f4b-nphfr            0m           2Mi             
bloaty-mcbloatface-7d7b64c65d-zw85p   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-9dvnm   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-p5cw2   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-f88xv   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-f2v5l   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-k6lgf   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-8hzfh   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-cmxzg   1m           2Mi             
bloaty-mcbloatface-7d7b64c65d-p9mgs   1m           2Mi             
canary-v2-6bdbfc4f4b-zcbzr            0m           2Mi             
canary-v2-6bdbfc4f4b-j2bxt            0m           2Mi             
canary-v2-6bdbfc4f4b-68w4k            0m           2Mi             
canary-v2-6bdbfc4f4b-nzqws            0m           2Mi             
canary-v2-6bdbfc4f4b-g55gv            0m           2Mi             
canary-v2-6bdbfc4f4b-lfdhq            0m           2Mi             
canary-v2-6bdbfc4f4b-dv6kb            0m           2Mi             
canary-v2-6bdbfc4f4b-8vgb7            0m           2Mi             
canary-v2-6bdbfc4f4b-2rh45            0m           2Mi             
canary-v2-6bdbfc4f4b-2ctpx            0m           2Mi           
    ```
