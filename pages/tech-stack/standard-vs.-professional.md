# Standard VS. Professional

Previously, it was a bit difficult to deploy FeatBit as it has too many dependencies. Many of them are not necessary for small businesses. So we introduced a lite version by removing the dependencies to ClickHouse, Kafka. We made the lite version as the default standard version and renamed the full version to FeatBit Professional.

* The standard version is ideal for small businesses, while the Professional version is ideal for medium and large businesses.
* Both the Standard and Professional versions are **scalable and fast**, and **have identical features**.
* The Standard version is a more **lightweight** option that only relies on Redis and MongoDB.
* The Professional version is **heavier** and depends on Redis, MongoDB, Kafka, and ClickHouse.
* Redis is the message queue of choice for the Standard version, while Kafka is used in the Professional version.
* MongoDB is the data analytics tool of choice for the Standard version, while ClickHouse is used in the Professional version.

