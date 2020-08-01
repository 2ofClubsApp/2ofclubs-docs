---
id: create_event
title: Create
sidebar_label: Create
---

export const Endpoint = ({children, color}) => ( <span style={{
      borderRadius: '2px',
      color: '#E83E8C',
    }}>{children}</span> );

<Endpoint>POST /clubs/{"{clubID}"}/events</Endpoint>: Creating a club event <br></br>

**Note**: Only a club owner or club managers can create a club event

```json
{ 
    "Name": string,
    "Description": string,
    "Location": string,
    "Fee": number
}
```

### Example Request
This is a **protected route**, a **valid JWT is required** in the header field
#### Header
```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1OTU4MjQyNzUsImlhdCI6IjIwMjAtMDctMjdUMDA6MjY6MTUuNzg5NTg0Mi0wNDowMCIsInN1YiI6ImNocmlzIn0.5US2_ITKcfgkpEbfsR-gxXbGPFY6XsgJPcGA5qaBD1M
```

#### Body
```json
{ 
    "Name": "Fantastic Event",
    "Description": "A very good event",
    "Location": "In-Person",
    "Fee": 30
}
```

### Parameters
---
**Name** (Required)

Min: 1 character <br></br>
Max: 50 characters

---
**Description** (Required)

Min: 0 characters <br></br>
(**Note**: If no description is specified, then the `Description` field would be left as `"Description": ""`)<br></br>
Max: 300 characters

---
**Location** (Required)

Min: 0 characters <br></br>
(**Note**: If no location is specified, then the `Location` field would be left as `"Location": ""`)<br></br>
Max: 300 characters

---
**Fee** (Required)

Value: The event fee must be greater or equal to 0 

---
### Possible Responses
#### Immediate Success
```json
{
	"Code": 1,
	"Message": "Successfully created event",
	"Data": {}
}
```
#### Failure
```json
{
	"Code": -1,
	"Message": "Club Not Found",
	"Data": {}
}
```
```json
{
	"Code": -1,
	"Message": "Unable to create event",
	"Data": {
		"Name": "Event name must be at least 1 character and a maximum of 50 characters",
		"Description": "Event description must be a maximum of 300 characters or less",
		"Location": "Event location must be a maximum of 100 characters or less",
		"Fee": "Fee must be greater or equal to $0"
	}
}
```


