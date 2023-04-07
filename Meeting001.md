Please design DB TABLES and RELATIONS for Meeting Project.
Each Meeting has a date, start time, venue and memo.

---

answer it again in html table and ol li html5 tags

---

<!DOCTYPE html>
<html>
<head>
<style>
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
    padding: 5px;
  }
</style>
</head>
<body>

<h2>1. Table: Venues</h2>
<table>
  <tr>
    <th>Column</th>
    <th>Data Type</th>
    <th>Constraint</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>venue_id</td>
    <td>INT</td>
    <td>PRIMARY KEY</td>
    <td>Unique venue ID</td>
  </tr>
  <tr>
    <td>venue_name</td>
    <td>VARCHAR</td>
    <td>NOT NULL</td>
    <td>Venue name</td>
  </tr>
  <tr>
    <td>venue_address</td>
    <td>VARCHAR</td>
    <td>NOT NULL</td>
    <td>Venue address</td>
  </tr>
</table>

<h2>2. Table: Users (Optional)</h2>
<table>
  <tr>
    <th>Column</th>
    <th>Data Type</th>
    <th>Constraint</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>user_id</td>
    <td>INT</td>
    <td>PRIMARY KEY</td>
    <td>Unique user ID</td>
  </tr>
  <tr>
    <td>username</td>
    <td>VARCHAR</td>
    <td>NOT NULL</td>
    <td>User's name</td>
  </tr>
  <tr>
    <td>email</td>
    <td>VARCHAR</td>
    <td>NOT NULL</td>
    <td>User's email address</td>
  </tr>
</table>
