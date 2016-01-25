# client config

Once Ansible has run you have a 3 broker cluster
with a zookeeper and schema registry on each node.

Most clients are going to want to know their details.

# NB: these docs cover Vagrant, check your inventory for other hostnames.

If you used the hostmanager plugin, names should resolve fine.


# zookeeper url

Consumers tend to use this.

    broker1:2181,broker2:2181,broker3:2181

# kafka url

Producers in 0.8 no longer have a zookeper dependency. Instead, you need to provide 
a list of brokers (can just be one - the client discovers the full list from the
first broker it finds):

    broker1:9092,broker2:9092,broker3:9092

# schema registry

They all run on port 8081 on each broker. All state is stored in the *_schemas* topic
or zookeeper, so it shouldn't matter which one you use.
