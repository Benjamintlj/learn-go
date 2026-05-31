# learn-go
This project is to teach me how to use Go, project structure and overall flow.
The point is that it's supposed to be low complexity. The challenge is learning 
writing notes, and understanding what works and what does not.

## Goal

- [ ] Create simple CRUD api, with stub responses
- [ ] Integrate a postgres DB
- [ ] Export holidays to a CSV and send it off
- [ ] Create a test suite

### HTTP interface
```text
POST   /people
GET    /people/{id}
PUT    /people/{id}
DELETE /people/{id}

POST   /holidays
GET    /holidays/{id}
PUT    /holidays/{id}
DELETE /holidays/{id}

GET    /holidays
GET    /holidays/export
```

### DB schema

Person Table
- Id
- Name
- Age

Holiday Table
- Id
- PersonId
- Location
- StartDate
- EndDate

## Structure
```
learn-go
├── README.md                   - Overview of project
└── src                         - Contains all Go code
    ├── cmd                     - Commands
    │   └── api-server          - Contains command to start service
    └── internal                - Internal packages, sorted by feature
        ├── people              - Anything related to people
        ├── holiday             - Anything related to holiday
        └── model               - Models
```