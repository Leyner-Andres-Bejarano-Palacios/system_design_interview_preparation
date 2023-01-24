# system_design_interview_preparation
this is the third installment in the series of repos "interview preparation", this time I will use a group of question to make a summary of the book Designing Data-Intensive Applications


## Theorical Questions Section

### Theorical Question 1

Do you know what telemetry is ?

<details><summary><b>Answer</b></summary>

Getting clear monitoring, such as performance metrics and error rates. This is referred to as telemetry

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 10
</details>

### Theorical Question 2

Do you understand what a load parameter is (this question can be ambigious so, how do you know for example that you need to increase or decrease the resources of your system) ?

<details><summary><b>Answer</b></summary>

We need to succinctly describe the current load on the system; only then can we
discuss growth questions (what happens if our load doubles?). Load can be described
with a few numbers which we call load parameters. The best choice of parameters
depends on the architecture of your system: it may be requests per second to a web
server, the ratio of reads to writes in a database, the number of simultaneously active
users in a chat room, the hit rate on a cache, or something else. Perhaps the average
case is what matters for you, or perhaps your bottleneck is dominated by a small
number of extreme cases.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 11
</details>

### Theorical Question 3

Do you understand what scaling up or vertical scaling and the difference with scaling out horizontal scaling?

<details><summary><b>Answer</b></summary>

scaling up (vertical scaling, moving to a
more powerful machine) and scaling out (horizontal scaling, distributing the load
across multiple smaller machines).

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 17
</details>


### Theorical Question 4

In computer science what is an abstraction.

<details><summary><b>Answer</b></summary>

One of the best tools we have for removing accidental complexity is abstraction. A
good abstraction can hide a great deal of implementation detail behind a clean,
simple-to-understand façade. A good abstraction can also be used for a wide range of
different applications.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 21
</details>

### Theorical Question 5

Do you understand when is the best case for representing our data in JSON file and when should we use a database like mongoDB

<details><summary><b>Answer</b></summary>

For a data structure like a résumé, which is mostly a self-contained document, a JSON
representation can be quite appropriate: see Example 2-1. JSON has the appeal of
being much simpler than XML. Document-oriented databases like MongoDB [9],
RethinkDB [10], CouchDB [11], and Espresso [12] support this data model.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 31
</details>

### Theorical Question 6

Do you understand what locallity is and why it helps databases like mongo achive higher performance than relational databases

<details><summary><b>Answer</b></summary>

The JSON representation has better locality than the multi-table schema. If you want to fetch a profile in the relational example, you need to either
perform multiple queries (query each table by user_id ) or perform a messy multi-
way join between the users table and its subordinate tables. In the JSON representa‐
tion, all the relevant information is in one place, and one query is sufficient.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 33
</details>

### Theorical Question 7

Do you understand what normalization means

<details><summary><b>Answer</b></summary>

If that information is duplicated, all the redundant copies need to be
updated. That incurs write overheads, and risks inconsistencies (where some copies
of the information are updated but others aren’t). Removing such duplication is the
key idea behind normalization in databases. ii

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 33
</details>

### Theorical Question 8

when would you use a relational model instead of a nosql database ?

<details><summary><b>Answer</b></summary>

The main arguments in favor of the document data model are schema flexibility, bet‐
ter performance due to locality, and that for some applications it is closer to the data
structures used by the application. The relational model counters by providing better
support for joins, and many-to-one and many-to-many relationships.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 38
</details>

### Theorical Question 8

Given the fact that we don't know when we will need to do a achnge in the schema, do you think that we will need a nosql database instead of a relationa one ?

<details><summary><b>Answer</b></summary>

Schema changes have a bad reputation of being slow and requiring downtime. This
reputation is not entirely deserved: most relational database systems execute the
ALTER TABLE statement in a few milliseconds. MySQL is a notable exception—it
copies the entire table on ALTER TABLE , which can mean minutes or even hours of
downtime when altering a large table.

Running the UPDATE statement on a large table is likely to be slow on any database,
since every row needs to be rewritten. If that is not acceptable, the application can
leave first_name set to its default of NULL and fill it in at read time, like it would with
a document database.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 40
</details>


### Theorical Question 9

Do you understand the difference between declarative and imperating programming ?

<details><summary><b>Answer</b></summary>

An imperative language tells the computer to perform certain operations in a certain
order. You can imagine stepping through the code line by line, evaluating conditions,
updating variables, and deciding whether to go around the loop one more time.

In a declarative query language, like SQL or relational algebra, you just specify the
pattern of the data you want—what conditions the results must meet, and how you
want the data to be transformed (e.g., sorted, grouped, and aggregated)—but not how
to achieve that goal. It is up to the database system’s query optimizer to decide which
indexes and which join methods to use, and in which order to execute various parts
of the query.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 43
</details>

### Theorical Question 10

Do you know what a pure function is ?

<details><summary><b>Answer</b></summary>

They must be pure functions, which means they only use the data that is passed to
them as input, they cannot perform additional database queries, and they must not
have any side effects. These restrictions allow the database to run the functions any‐
where, in any order, and rerun them on failure.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 48
</details>

### Theorical Question 11

when would you use a grapgh like model ?

<details><summary><b>Answer</b></summary>

If your application has mostly one-to-many relationships (tree-structured data) or no relationships between records, the document
model is appropriate.

But what if many-to-many relationships are very common in your data? The relational model can handle simple cases of many-to-many relationships, but as the connections within your data become more complex, it becomes more natural to start modeling your data as a graph.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 49
</details>

### Theorical Question 12

In databases what an Index is ?

<details><summary><b>Answer</b></summary>

In order to efficiently find the value for a particular key in the database, we need a
different data structure: an index. In this chapter we will look at a range of indexing
structures and see how they compare; the general idea behind them is to keep some
additional metadata on the side, which acts as a signpost and helps you to locate the
data you want. If you want to search the same data in several different ways, you may
need several different indexes on different parts of the data.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 71
</details>

### Theorical Question 12

Do you know what hash indexes are ?

<details><summary><b>Answer</b></summary>

Key-value stores are quite similar to the dictionary type that you can find in most
programming languages, and which is usually implemented as a hash map Whenever you append a
new key-value pair to the file, you also update the hash map to reflect the offset of the
data you just wrote (this works both for inserting new keys and for updating existing
keys). When you want to look up a value, use the hash map to find the offset in the
data file, seek to that location, and read the value.

This may sound simplistic, but it is a viable approach. In fact, this is essentially what
Bitcask (the default storage engine in Riak) does [3]. Bitcask offers high-performance
reads and writes, subject to the requirement that all the keys fit in the available RAM,
since the hash map is kept completely in memory.

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 72
</details>

### Theorical Question 13

Do you know what a transactional database or OLTP is ?

<details><summary><b>Answer</b></summary>

Even though databases started being used for many different kinds of data—comments on blog posts, actions in a game, contacts in an address book, etc.—the basic
access pattern remained similar to processing business transactions. An application
typically looks up a small number of records by some key, using an index. Records
are inserted or updated based on the user’s input. Because these applications are
interactive, the access pattern became known as online transaction processing
(OLTP).

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 92
</details>

### Theorical Question 13

Do you know what a analitical database or OLAP is ?

<details><summary><b>Answer</b></summary>

databases also started being increasingly used for data analytics, which has
very different access patterns. Usually an analytic query needs to scan over a huge
number of records, only reading a few columns per record, and calculates aggregate
statistics (such as count, sum, or average) rather than returning the raw data to the
user. For example, if your data is a table of sales transactions, then analytic queries
might be:
• What was the total revenue of each of our stores in January?
• How many more bananas than usual did we sell during our latest promotion?
• Which brand of baby food is most often purchased together with brand X
diapers?

These queries are often written by business analysts, and feed into reports that help
the management of a company make better decisions (business intelligence). In order
to differentiate this pattern of using databases from transaction processing, it has
been called online analytic processing (OLAP)

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 92
</details>


### Theorical Question 14

Do you know the difference between OLAP and OLTP ?

<details><summary><b>Answer</b></summary>

![Image](img/OLTPvsOLAP.png "OLTP vs OLAP")

</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 91
</details>


### Theorical Question 15

Do you know the star-schema is ?

<details><summary><b>Answer</b></summary>

Many data warehouses are used in a fairly formulaic style, known as a star schema (also known as dimensional modeling [55]).

The example schema the Figure below shows a data warehouse that might be found at a
grocery retailer. At the center of the schema is a so-called fact table (in this example,
it is called fact_sales ). Each row of the fact table represents an event that occurred
at a particular time (here, each row represents a customer’s purchase of a product). If
we were analyzing website traffic rather than retail sales, each row might represent a
page view or a click by a user.

![Image](img/star_schema.png "star schema")

A variation of this template is known as the snowflake schema, where dimensions are
further broken down into subdimensions. For example, there could be separate tables
for brands and product categories, and each row in the dim_product table could ref‐
erence the brand and category as foreign keys, rather than storing them as strings in
the dim_product table.



</details>

<details><summary><b>Source</b></summary>
Designing Data-Intensive Applications - pag 91
</details>
