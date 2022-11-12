Splunk
======

Part of the Blue Primer series, learn how to use Splunk to search through massive amounts of information.

## 1. Deploy!

### (1)

_Deploy the virtual machine and connect to the website found at MACHINE_IP:8000_

> N/A

### (2)

_Move on to the quiz while Splunk loads_

> N/A

## 2. Can you dig it?

- https://www.splunk.com/content/dam/splunk2/pdfs/solution-guides/splunk-quick-reference-guide.pdf
- https://www.splunk.com/en_us/blog/security/hunting-with-splunk-the-basics.html
- Lockheed Martin cyber kill chain
- MITRE ATT&CK framework
- Suricata: IDS (Intrusion Detection System)
- https://robtex.com/ : domain and IP research
- https://threatcrowd.com/ : domain and IP visualization
- https://virustotal.com/ : malware recognition + passive DNS resolution
- https://www.splunk.com/en_us/blog/tips-and-tricks/work-flow-ing-your-osint.html

### (1)

_Splunk queries always begin with this command implicitly unless otherwise specified.
What command is this? When performing additional queries to refine received data this
command must be added at the start. This is a prime example of a slight trick question._

> search

### (2)

_When searching for values, it's fairly typical within security to look for uncommon
events. What command can we include within our search to find these?_

> rare

### (3)

_What about the inverse? What if we want the most common security event?_

> top

### (4)

_When we import data into splunk, what is it stored under?_

> index

### (5)

_We can create 'views' that allow us to consistently pull up the same search
over and over again; what are these called?_

> dashboard

### (6)

_Importing data doesn't always go as planned and we can sometimes end up with multiple
copies of the same data, what command do we include in our search to remove these copies?_

> dedup

### (7)

_Splunk can be used for more than just a SIEM and it's commonly used in marketing to
track things such as how long a shopping trip on a website lasts from start to finish.
What command can we include in our search to track how long these event pairs take?_

> transaction

### (8)

_In a manner similar to Linux, we can 'pipe' search results into further commands,
what character do we use for this?_

> |

### (9)

_In performing data analytics with Splunk (ironically what the tool is at it's core) it's
useful to track occurrences of events over time, what command do we include to plot this?_

> timechart

### (10)

_What about if we want to gather general statistical information about a search?_

> stats

### (11)

_Data imported into Splunk is categorized into columns called what?_

> fields

### (12)

_When we import data into Splunk we can view it's point of origination, what
is this called? I'm looking for the machine aspect of this here._

> host

### (13)

_When we import data into Splunk we can view its point of origination
from within a system, what is this called?_

> source

### (14)

_We can classify these points of origination and group them all together, viewing them as
their specific type. What is this called? Use the syntax found within the search query
rather than the proper name for this._

> sourcetype

### (15)

_When performing functions on data we are searching through we use a specific
command prior to the evaluation itself, what is this command?_

> eval

### (16)

_Love it or hate it regular expression is a massive component to Splunk,
what command do we use to specific regex within a search?_

> rex

### (17)

_It's fairly common to create subsets and specific views for less
technical Splunk users, what are these called?_

> pivot table

### (18)

_What is the proper name of the time date field in Splunk?_

> _time

### (19)

_How do I specifically include only the first few values found within my search?_

> head

### (20)

_More useful than you would otherwise imagine, how do I flip the order that results are returned in?_

> reverse

### (21)

_When viewing search results, it's often useful to rename fields using user-provided
tables of values. What command do we include within a search to do this?_

> lookup

### (22)

_We can collect events into specific time frames to be used in further processing.
What command do we include within a search to do just that?_

> bucket

### (23)

_We can also define data into specific sections of time to be used within chart commands, what
command do we use to set these lengths of time? This is different from the previous question
as we are no longer collecting for further processing._

> span

### (24)

_When producing statistics regarding a search it's common to number the occurrences of an event,
what command do we include to do this?_

> count

### (25)

_Last but not least, what is the website where you can find the Splunk apps at?_

> splunkbase.splunk.com

### (26)

_We can also add new features into Splunk, what are these called?_

> apps

### (27)

_What does SOC stand for?_

> security operations center

### (28)

_What does SIEM stand for?_

>security information and event management

### (29)

_How about BOTS?_

>boss of the soc

### (30)

_And CIM?_

>common information model

### (31)

_What is the website where you can find the Splunk forums at?_

> community.splunk.com

## 3. BOTS!

### (1)

_Check out BOTS!_

> N/A

## 4. Halp, I'm drowning in logs!

### (1)

_Read the overview!_

> N/A

## 5. Advanced Persistent Threat
