
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


### GPT-3.5

<pre>
CREATE TABLE Meeting (
  id INT IDENTITY(1,1) PRIMARY KEY,
  date DATE NOT NULL,
  start_time DATETIME NOT NULL,
  venue VARCHAR(255) NOT NULL,
  memo VARCHAR(MAX) NOT NULL
);

CREATE TABLE Role (
  id INT IDENTITY(1,1) PRIMARY KEY,
  name VARCHAR(255) UNIQUE NOT NULL,
  description VARCHAR(MAX) NOT NULL
);

CREATE TABLE Member (
  id INT IDENTITY(1,1) PRIMARY KEY,
  name VARCHAR(255) UNIQUE NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL
);

CREATE TABLE Assignment (
  id INT IDENTITY(1,1) PRIMARY KEY,
  meeting_id INT NOT NULL,
  role_id INT NOT NULL,
  seq INT NOT NULL,
  member_id INT NOT NULL,
  CONSTRAINT unique_assignment UNIQUE (meeting_id, role_id, seq),
  CONSTRAINT fk_assignment_meeting FOREIGN KEY (meeting_id) REFERENCES Meeting(id),
  CONSTRAINT fk_assignment_role FOREIGN KEY (role_id) REFERENCES Role(id),
  CONSTRAINT fk_assignment_member FOREIGN KEY (member_id) REFERENCES Member(id)
);

CREATE TABLE Speech (
  id INT IDENTITY(1,1) PRIMARY KEY,
  assignment_id INT NOT NULL,
  level VARCHAR(255) NOT NULL,
  title VARCHAR(255) NOT NULL,
  memo VARCHAR(MAX) NOT NULL,
  CONSTRAINT fk_speech_assignment FOREIGN KEY (assignment_id) REFERENCES Assignment(id)
);

-- Insert initial data
INSERT INTO Meeting (date, start_time, venue, memo) VALUES 
('2023-04-06', '2023-04-06 19:00:00', 'wtc0406', 'wtc0406 memo'),
('2023-04-20', '2023-04-20 19:00:00', 'wtc0420', 'wtc0420 memo');

INSERT INTO Role (name, description) VALUES 
('Toastmaster', 'Responsible for conducting the meeting'),
('Table Topic Master', 'Responsible for Table Topics session'),
('General Evaluator', 'Evaluates the overall meeting'),
('Speaker', 'Gives a prepared speech'),
('Evaluator', 'Evaluates a prepared speech'),
('Warm up', 'Leads the Warm up session'),
('Receptionist', 'Greets and checks in guests'),
('Captain', 'Manages the meeting from the back of the room'),
('Timer', 'Times each speech and provides signals'),
('Word Master', 'Introduces a word to be used throughout the meeting'),
('Ah-Counter', 'Counts filler words used during the meeting'),
('Vote-Counter', 'Counts votes during the meeting'),
('Grammarian', 'Introduces a grammar rule and monitors its usage during the meeting'),
('Photographer', 'Takes photos during the meeting'),
('President', 'Leads the club');

INSERT INTO Member (name, email) VALUES
('Aden Lu', 'aden.lu@example.com'),
('Ben Kang', 'ben.kang@example.com'),
('Candy Hsu', 'candy.hsu@example.com'),
('Cory Chen', 'cory.chen@example.com'),
('Dan Lin', 'dan.lin@example.com'),
('David Chang', 'david.chang@example.com'),
('Gimmy Chiu', 'gimmy.chiu@example.com'),
('Hank Tsai', 'hank.tsai@example.com'),
('Jenny Lin', 'jenny.lin@example.com'),
('Kevin Wang', 'kevin.wang@example.com'),
('Lien Wei', 'lien.wei@example.com'),
('Mark Chen', 'mark.chen@example.com'),
('Meng-Wei Lin', 'meng-wei.lin@example.com'),
('Renee Chen', 'renee.chen@example.com'),
('Sharry Wu', 'sharry.wu@example.com'),
('Wade Kaardal', 'wade.kaardal@example.com'),
('Yuying Pai', 'yuying.pai@example.com'),
('Yvonne Lin', 'yvonne.lin@example.com'),
('Lisa Fang', 'lisa.fang@example.com'),
('Riri', 'riri@example.com');


</pre>
