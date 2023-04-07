Please design DB TABLES and RELATIONS, in MS SQL script, for a Toastmaster Regular Meeting Agenda Project. 

All id must be identifier.

Entity Meeting has a date, start time (as datetime), venue and memo.
Entity Role has a name, seq, and description. Combination of name and seq must be unique
Entity Member has a name and email. Name must be unique. Email must be unique
Table Assignment keeps Meeting, Role and Member. Any given meeting has unique role and each role only allow assign to one member.

Table Speech based on Assignment, to have Level, Title and Memo

To have initial data as follows,
Meeting 2023-04-06, start time is 19:00, venue and memo both are wtc0406
Meeting 2023-04-20, start time is 19:00, venue and memo both are wtc0420

To have initial data for Role as follows,
role_name	seq
Toastmaster	1
Table Topic Master	1
General Evaluator	1
Speaker	1
Speaker	2
Speaker	3
Speaker	4
Evaluator	1
Evaluator	2
Evaluator	3
Evaluator	4
Warm up	1
Receptionist	1
Captain	1
Timer	1
Word Master	1
Ah-Counter	1
Vote-Counter	1
Grammarian	1
Photographer	1
President	1
Photographer	2

To have initial data for Member as follows, and please put email as name( all lower case, replace space with dot, all in domain example.com)
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

<pre>
CREATE TABLE Meeting (
    id INT IDENTITY(1,1) PRIMARY KEY,
    meeting_date DATE NOT NULL,
    start_time DATETIME NOT NULL,
    venue VARCHAR(255) NOT NULL,
    memo VARCHAR(255)
);

CREATE TABLE Role (
    id INT IDENTITY(1,1) PRIMARY KEY,
    role_name VARCHAR(255) NOT NULL,
    seq INT NOT NULL,
    description VARCHAR(255),
    UNIQUE(role_name, seq)
);

CREATE TABLE Member (
    id INT IDENTITY(1,1) PRIMARY KEY,
    member_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL
);

CREATE TABLE Assignment (
    id INT IDENTITY(1,1) PRIMARY KEY,
    meeting_id INT NOT NULL,
    role_id INT NOT NULL,
    member_id INT NOT NULL,
    FOREIGN KEY(meeting_id) REFERENCES Meeting(id),
    FOREIGN KEY(role_id) REFERENCES Role(id),
    FOREIGN KEY(member_id) REFERENCES Member(id),
    UNIQUE(meeting_id, role_id)
);

CREATE TABLE Speech (
    id INT IDENTITY(1,1) PRIMARY KEY,
    assignment_id INT NOT NULL,
    level VARCHAR(255),
    title VARCHAR(255),
    memo VARCHAR(255),
    FOREIGN KEY(assignment_id) REFERENCES Assignment(id)
);

-- Insert initial data
INSERT INTO Meeting (meeting_date, start_time, venue, memo)
VALUES ('2023-04-06', '2023-04-06 19:00:00', 'wtc0406', 'wtc0406 memo'),
       ('2023-04-20', '2023-04-20 19:00:00', 'wtc0420', 'wtc0420 memo');

INSERT INTO Role (role_name, seq, description)
VALUES ('Toastmaster', 1, 'Toastmaster description'),
       ('Table Topic Master', 1, 'Table Topic Master description'),
       ('General Evaluator', 1, 'General Evaluator description'),
       ('Speaker', 1, 'Speaker 1 description'),
       ('Speaker', 2, 'Speaker 2 description'),
       ('Speaker', 3, 'Speaker 3 description'),
       ('Speaker', 4, 'Speaker 4 description'),
       ('Evaluator', 1, 'Evaluator 1 description'),
       ('Evaluator', 2, 'Evaluator 2 description'),
       ('Evaluator', 3, 'Evaluator 3 description'),
       ('Evaluator', 4, 'Evaluator 4 description'),
       ('Warm up', 1, 'Warm up description'),
       ('Receptionist', 1, 'Receptionist description'),
       ('Captain', 1, 'Captain description'),
       ('Timer', 1, 'Timer description'),
       ('Word Master', 1, 'Word Master description'),
       ('Ah-Counter', 1, 'Ah-Counter description'),
       ('Vote-Counter', 1, 'Vote-Counter description'),
       ('Grammarian', 1, 'Grammarian description'),
       ('Photographer', 1, 'Photographer 1 description'),
       ('President', 1, 'President description'),
       ('Photographer', 2, 'Photographer 2 description');

INSERT INTO Member (member_name, email)
VALUES ('Aden Lu', 'aden.lu@example.com'),
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



