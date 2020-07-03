In my Last ML Project, I got the chance to work with Pyspark on [Databricks](http://databricks.com). PySpark is a great language to learn in order to create more scalable analyses and pipelines. It was a difficult transition at the start since I am used to working with Pandas in Python and the wide range of functionality offered by Pandas. So during my stint with Pyspark, I discovered some very useful features which helps a lot when you have experience with Pandas. Mostly, I want to focus on two major features - [Koalas](https://koalas.readthedocs.io/en/latest/) and [Pandas UDF](https://databricks.com/blog/2017/10/30/introducing-vectorized-udfs-for-pyspark.html).

### Pandas UDF
Pandas UDFs allow data scientists not only to scale out their workloads, but also to leverage the Pandas APIs in Apache Spark. The user-defined functions are executed by:
- Apache Arrow, to exchange data directly between JVM and Python driver/executors with near-zero (de)serialization cost.
- Pandas inside the function, to work with Pandas instances and APIs.

The Pandas UDFs work with Pandas APIs inside the function and Apache Arrow for exchanging data. It allows vectorized operations that can increase performance up to 100x, compared to row-at-a-time Python UDFs.
