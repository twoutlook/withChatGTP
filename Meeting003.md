
### Requirement
<pre>
Please design DB TABLES and RELATIONS, in MS SQL script, for a Toastmaster Regular Meeting Agenda Project.

All id must be identifier.
Entity Meeting has a date, start time (as datetime), venue and memo. 
Entity Role has a name and description. Name must be unique .
Entity Member has a name and email. Name must be unique. Email must be unique. 
Table Assignment keeps Meeting, Role, Seq and Member. Any given meeting has unique combination of role and seq.
Table Speech based on Assignment, to have Level, Title and Memo
</pre>

### Initial Data

-- To have initial data as follows, 

<pre>
Meeting 2023-04-06, start time is 19:00, venue and memo both are wtc0406 
Meeting 2023-04-20, start time is 19:00, venue and memo both are wtc0420
</pre>

-- To have initial data for Role as follows,
<pre>
  role_name
  Toastmaster
  Table Topic Master
  General Evaluator
  Speaker
  Evaluator
  Warm up
  Receptionist
  Captain
  Timer
  Word Master
  Ah-Counter
  Vote-Counter
  Grammarian
  Photographer
  President
</pre>



-- To have initial data for Member as follows, and please put email as name( all lower case, replace space with dot, all in domain example.com) 
<pre>
member_name
Aden Lu
Ben Kang
Candy Hsu
Cory Chen
Dan Lin
David Chang
Gimmy Chiu
Hank Tsai
Jenny Lin
Kevin Wang
Lien Wei
Mark Chen
Meng-Wei Lin
Renee Chen
Sharry Wu
Wade Kaardal
Yuying Pai
Yvonne Lin
Lisa Fang
Riri
</pre>
