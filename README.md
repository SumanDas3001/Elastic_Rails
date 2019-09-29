
# Using Elasticsearch in a Rails application
### Install Elasticsearch

> Install Elasticsearch with Debian Package
```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.2-amd64.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.2-amd64.deb.sha512
shasum -a 512 -c elasticsearch-7.3.2-amd64.deb.sha512 
sudo dpkg -i elasticsearch-7.3.2-amd64.deb
```

- Elasticsearch is not started automatically after installation. How to start and stop Elasticsearch depends on whether your system uses SysV init or systemd (used by newer distributions). You can tell which is being used by running this command:

```
ps -p 1
```

> Running Elasticsearch with systemd

- To configure Elasticsearch to start automatically when the system boots up, run the following commands:
```
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
```
- Elasticsearch can be started and stopped as follows:

```
sudo systemctl start elasticsearch.service
sudo systemctl stop elasticsearch.service
```

- After the installation, just make sure to start the service if it’s not started.
- You can check that with curl http://localhost:9200.
- It should give something like:

```
{
  "name" : "asdfasdf",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "asasdfdf-as",
  "version" : {
    "number" : "6.0.0",
    "build_hash" : "asdf",
    "build_date" : "2017-11-10T18:41:22.859Z",
    "build_snapshot" : false,
    "lucene_version" : "7.0.1",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```
### Rails
> Elasticsearch gem
- We are going to use existing gems to integrate with elasticsearch, the elasticsearch-rails & elasticsearch-model gems.

- Open your Gemfile and add the following lines:
```
gem 'elasticsearch-model', '~> 7.0'
gem 'elasticsearch-rails', '~> 7.0'
```
- Now install this two gem
```
bundle
```











