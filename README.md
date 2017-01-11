## ELK Examples

I'll use this repo to save my progress while playing around with the ELK stack.

### Setup

You need to have [docker installed](https://docs.docker.com/engine/installation/). Clone the repo, and start this elk docker image:

```bash
docker run -p 5601:5601 -p 9200:9200 -p 5044:5044 -it --name elk sebp/elk
```

Look for a line similar to this in the running log to make sure the services are up an running in the container:

```
Successfully started Logstash API endpoint {:port=>9600}
```

Leave that console window open, and in a new one run the following script that will load up the initial test data into the
elasticsearch server:

```bash
cd data && sh load.sh
```

If everything went well, you should see the new list of indices created:

```
health status index               uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   logstash-2015.05.20 QvshRcIzSEaL9F8_RY_ySw   5   1       4750            0     26.5mb         26.5mb
yellow open   shakespeare         Sz2904JGS-OKoV5EHlSx9w   5   1     111396            0     28.3mb         28.3mb
yellow open   logstash-2015.05.19 5WQRIpPFTqOE3mXkBMRgeA   5   1       4624            0     30.4mb         30.4mb
yellow open   logstash-2015.05.18 KuDavcHNQgGBfE2ZV6cuLg   5   1       4631            0     29.3mb         29.3mb
yellow open   .kibana             3oJvvpnFQLKVS2MHL8cwNQ   1   1          1            0      3.1kb          3.1kb
yellow open   bank                DO6cKfcWQTCXbqK0jnnGBg   5   1       1000            0      651kb          651kb

```

After this is done, you can navigate to [http://localhost:5601](http://localhost:5601) and you'll be greeted by the kibana home page. At this point, you are all set to start the kibana tutorial from [this step](https://www.elastic.co/guide/en/kibana/current/tutorial-define-index.html) with all the initial setup already done.
