In my Last ML Project, I got the chance to work with Pyspark on [Databricks](http://databricks.com). PySpark is a great language to learn in order to create more scalable analyses and pipelines. It was a difficult transition at the start since I am used to working with Pandas in Python and the wide range of functionality offered by Pandas. But Pandas does not scale well to big data as it does not parallelize jobs for you while Spark has become the de facto standard for big data processing. So during my stint with Pyspark, I discovered some very useful features which helps a lot when you have experience with Pandas. Mostly, I want to focus on two major features - [Koalas](https://koalas.readthedocs.io/en/latest/) and [Pandas UDF](https://databricks.com/blog/2017/10/30/introducing-vectorized-udfs-for-pyspark.html).

### Pandas UDF
Pandas UDFs allow data scientists not only to scale out their workloads, but also to leverage the Pandas APIs in Apache Spark. The user-defined functions are executed by:
- Apache Arrow, to exchange data directly between JVM and Python driver/executors with near-zero (de)serialization cost.
- Pandas inside the function, to work with Pandas instances and APIs.

The Pandas UDFs work with Pandas APIs inside the function and Apache Arrow for exchanging data. It allows vectorized operations that can increase performance up to 100x, compared to row-at-a-time Python UDFs. For performance comparison between row-at-a-time UDFs and Pandas UDFs, you can have a look at [this](https://databricks.com/blog/2017/10/30/introducing-vectorized-udfs-for-pyspark.html).

I stumbled across Pandas UDF while searching for efficient implementation of Linear Regression over grouped data in Pyspark. For my use case, I needed to train multiple Linear Regression Models and all my pythonic mind could think was nested for loops for filtering data and training Regression Model for every dataset. Not to mention, the same inefficient way to be used for Prediction as well. Anybody who is new to Spark might take some time to realize that Loops are very bad practice in Spark due to lazy evaluation. For better explanation, check [this](https://stackoverflow.com/questions/54305007/pyspark-lazy-evaluation-in-loops-too-slow) out.

### Koalas
Koalas is an open source project that augments PySpark’s DataFrame API to make it compatible with pandas. For work that was initially written in pandas for a single machine, Koalas allows data scientists to scale up their code on Spark by simply switching out pandas for Koalas.

