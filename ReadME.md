## Event Tracker

### The Problem:

I help with the organisation of a large national scout camp. It is a weekend camp where we have 6 activity zones each with a variety of different activities in each of the zones. As most people know Scouts work towards badges. We have always had a problem that we can’t keep track of the activities that the young people have done so they can count towards each of the participants badges and awards. I think it would be awesome if we could record this and pass the information back to the leaders so they can get the young people the credit they deserve.

### Possible solutions:

#### Low tech solution:
Create physical paper passports and stickers for each activity so that upon completion of the activity they get the sticker.
Issues with this are it doesn’t feel very sustainable + it is creating a lot of work for the individual volunteers who oversee the young people.

#### Techie solutions: 
Create a web form where each young person could scan the QR code for the activity and submit that when they complete each activity like you do for each LFT you fill in

Issues, there is a lot of expectation for them to all have phones and also the wifi is patchy which would stop them being able to use it.


So a combo of the low tech and the Tech solution seems like the best approach. 
If the participant has a QR code with a ID code and each activity has a QR code with an activity ID. Then we have a web form to take in two fields that can be populated by qr code

So Database wise we would need a couple of tables:

##### Tracker table
| Column Name	| SubmissionID |	Captured |	Participant ID |	Activity ID |
| Type	| PrimaryKey Int |	DateTime |	INT |	INT |
| Description |	Unique ID per submission |	The time the form was submitted |	Identifier for each Participant |	Identifier for each activity |

##### Activity Table
| Column Name |	ActivityID	| Activity Name |	Zone |	Achievements |
| Type |	PrimaryKey Int |	String |	String |	String |
| Description |	Unique ID per Activity |	The name of the activity |	The Zone the activity is in |	The badge areas covered by each award |

##### Participant Table
| Column Name |	ParticipantID |	ScoutGroup |
| Type |	PrimaryKey Int |	String |
| Description |	Unique ID per Participant |	The name of the group they belong to |

This table is particularly spars as it helps us with GDPR and data security, If the leader keeps a record of there troops worth of ID numbers, I we send them a report of badges covered by participantID then they can re match up. 

##### Viewing activities completed

We can create a view where we join the tables and un pivot the tracker table which will give a breakdown of the activities completed by participant giving us there badges achieved column.

| Column Name |	ParticipantID |	ScoutGroup |	Badge Achievements |
| Type |	PrimaryKey Int |	String |	String |
| Description |	Unique ID per Participant | The name of the group they belong to |	The areas they covered |


QR scanner code for website
https://blog.minhazav.dev/research/html5-qrcode

