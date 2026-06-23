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

## Learning Docs

| Topic              | links                                                                                                                                                                                                                                                         |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| net/http           | https://pkg.go.dev/net/http<br/>- http.HandleFunc / http.Handle — registering routes<br/>- http.Request — reading the URL, body, headers<br/>- http.ResponseWriter — writing status codes and response bodies<br/>- http.ListenAndServe — starting the server |
| encoding/json      | https://pkg.go.dev/encoding/json<br/>- json.NewDecoder(r.Body).Decode(&v) — parsing request bodies<br/>- json.NewEncoder(w).Encode(v) — writing responses<br/>- Struct tags: json:"name" — how Go maps struct fields to JSON keys                             |
| database/sql + pgx | https://pkg.go.dev/database/sql<br/>You will also need the [postgres driver](https://github.com/jackc/pgx)<br/>- sql.Open, db.QueryRow, db.Exec, db.Query<br/>- Scanning rows into structs with .Scan()<br/>- Handling sql.ErrNoRows                          |
| encoding/csv       | https://pkg.go.dev/encoding/csv<br/>- csv.NewWriter, w.Write([]string{...}), w.Flush()                                                                                                                                                                        |
| Testing            | https://pkg.go.dev/testing<br/>- Writing a TestXxx(t *testing.T) function<br/>- t.Errorf, t.Fatalf<br/>- Running with go test ./...                                                                                                                           |