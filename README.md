# JSONQL
A Universal Query Language based on JSON

## About
This project aims to provide a way to universaly define queries that can be used to:
- Actually query existing data at runtime;
- Be a intermediary between language diallects (Ex.: Language A -> JSONQL -> Language B);
- Be used as documentation of conditions (Ex.: Said API endpoint returns user entities that match said JSONQL Query).

JSONQL does not compete with JSON Schema. JSON Schema's speciality is to define data structure, while JSONQL's
speciality is to query actual data of any complexity.

## Specification

### The Query Object
See [the schema](schema/query.schema.json)

### The Property Locator
A value locator is a string used to identify a property or a set of properties in a dataset structure.

Example structure:

```json
[
    {
        "id": 1,
        "users": [
            {
                "id": 1,
                "name": "John",
                "age": 31
            }, {
                "id": 2,
                "name": "Marie",
                "age": 42
            }
        ]
    }, {
        "id": 2,
        "users": [
            {
                "id": 3,
                "name": "Albert",
                "age": 18
            }
        ]
    },
]
```

Example Property Locators:
- "users": The "users" of the objects in the root array;
- "users.name": The "name" property of the objects in the "users" arrays;
- "!users.id": All the properties except for "id" of the objects in the "users" arrays.

## The response
The response of a query is expected to be an array of objects.

When querying a single object, the array will contain the single object.

When querying a single value, the array will contain a single object with the single property.