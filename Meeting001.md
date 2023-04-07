Please design DB TABLES and RELATIONS for Meeting Project.
Each Meeting has a date, start time, venue and memo.




<table>
  <thead>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Constraint</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
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
  </tbody>
</table>
