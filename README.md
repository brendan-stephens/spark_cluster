# spark_cluster_vagrant #
Vagrant template to provision a Spark cluster with lean defaults. 

# Details #

- See `Vagrantfile` for details and to make changes.
- Spark running as a standalone cluster. Tested with Spark 2.1.x (check Spark Connector Compatability).
- One head node Centos 7.4 machine and `N` worker (slave) machines.
- Spark running in standalone cluster mode.

# Usage 

* Clone this repository first.

* [Download a pre-built Spark package](https://spark.apache.org/downloads.html) and place it into this directory; symlink as "spark.tgz".

* [Download the Spark Connector](https://network.pivotal.io/products/pivotal-gpdb) and place it into this directory.

* [Optional: Download the PostgreSQL JDBC Driver](https://jdbc.postgresql.org/download.html).

* Open up `Vagrantfile` in a text editor.

* Change the `N_WORKERS` to the number of desired worker hosts [0-9].

* Vagrant will spin up one "head node" and `N` worker nodes in a Spark standalone cluster.

* Feel free to make other changes, e.g. RAM and CPU for each of the machines.

* When you're ready, just run `vagrant up` in the directory the `Vagrantfile` is in. 

# Testing

* SSH in using `vagrant ssh hn0` or `vagrant ssh wn0`.

* The Spark WebUI should be available at `http://192.168.99.200:8080`.

* To run `SparkPi` on the cluster, run the following commands:

    vagrant ssh hn0
    spark-submit --class org.apache.spark.examples.SparkPi ~/spark/examples/jars/spark-examples_2.11-2.2.1.jar 1000


# Cleanup

* Shut down the cluster with `vagrant halt` and delete it with `vagrant destroy`. 

* You can always run `vagrant up` to turn on or build a brand new cluster.

# License #

See the LICENSE.txt file.
