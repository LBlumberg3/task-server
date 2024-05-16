# Task Server
Basic CRUD API for simple data elements, "tasks", with (initially) a single kind of SQL table associated with it

## Task Data Models
The data models used in this API are described here
```
type Task {
    id: Int!,
    title: String!
    description: String!
    author: String!
    assignee: String
    type: TaskType!
    status: TaskStatus!
    createTs: String!
    lastChangeTs: String
}

enum TaskType {
    APPOINTMENT, CLEANING, COOKING, ERRAND, EXERCISE, MISCELLANEOUS  
}

enum TaskStatus {
    CREATED, ACCEPTED, IN_PROGRESS, COMPLETE, CONFIRMED
    # CREATED == record exists, ACCEPTED == task assignment was accepted by assignee
    # IN_PROGRESS is self-explanatory, COMPLETE == when assignee is ready for review of task
    # CONFIRMED is when author assigns and closes task 
}
```

## API Endpoints
The API will expose four endpoints for CRUD functions using `POST`, `GET`, `PUT|PATCH`, and `DELETE` verbs respectively, under the `{FQDN}/task/*` path