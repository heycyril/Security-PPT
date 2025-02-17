Discovering patterns of activity in unstructured incident reports at scale
Bronwyn Woods*, Sam Perl
* blwoods@cert.org
Software Engineering Institute Carnegie Mellon University Pittsburgh, PA 15213

� 2015 Carnegie Mellon University

Copyright 2015 Carnegie Mellon University
This material is based upon work funded and supported by Department of Homeland Security under Contract No. FA8721-05-C-0003 with Carnegie Mellon University for the operation of the Software Engineering Institute, a federally funded research and development center sponsored by the United States Department of Defense.
NO WARRANTY. THIS CARNEGIE MELLON UNIVERSITY AND SOFTWARE ENGINEERING INSTITUTE MATERIAL IS FURNISHED ON AN "AS-IS" BASIS. CARNEGIE MELLON UNIVERSITY MAKES NO WARRANTIES OF ANY KIND, EITHER EXPRESSED OR IMPLIED, AS TO ANY MATTER INCLUDING, BUT NOT LIMITED TO, WARRANTY OF FITNESS FOR PURPOSE OR MERCHANTABILITY, EXCLUSIVITY, OR RESULTS OBTAINED FROM USE OF THE MATERIAL. CARNEGIE MELLON UNIVERSITY DOES NOT MAKE ANY WARRANTY OF ANY KIND WITH RESPECT TO FREEDOM FROM PATENT, TRADEMARK, OR COPYRIGHT INFRINGEMENT.
This material has been approved for public release and unlimited distribution.
This material may be reproduced in its entirety, without modification, and freely distributed in written or electronic form without requesting formal permission. Permission is required for any other use. Requests for permission should be directed to the Software Engineering Institute at permission@sei.cmu.edu.
CERT� is a registered mark of Carnegie Mellon University.
DM-0002418

Discovering patterns of activity in incident reports

2

Goal: From tickets to cyber landscape
� US-CERT receives incident reports from a diverse constituency. � Each ticket is an observation of problematic activity by a
particular reporter. � Taken en masse, we use the tickets as as a statistical sample of
observations to learn about the threat and defense landscape. � Specifically, we infer similarity relationships and functional
clusters of indicators using information about reporting patterns.

Threat actors

International partners

Agency infrastructure

Agency response
teams

Malware class
US-CERT

Compromised Common

website

reference

infrastructure

websites

Phishing

campaign

Landscape

Observation

Inference

Tickets

Discovering patterns of activity in incident reports

3

Some approaches
Extract indicators and exploit reporting patterns across agencies and tickets. � Indicator similarity � Indicator communities
Parse free text descriptions of incidents for tagging, topic modeling, and information extraction. � Exploit regularities in the format of tickets from individual
reporters � Infer and extract frequently reported information
e.g. cost of incident, resolution status, impact � More value in tickets without extra cost to reporters.

Discovering patterns of activity in incident reports

4

Data Description

This dataset consists of incident tickets from 2013. Each ticket has:

Structured Fields: � Reporter information � Category, subcategory � Date of submission � Information about US-CERT ticket processing: assigned group,
closure status

Unstructured Field: � Notes (free text allowed)

The unstructured notes field contains most of the information about each ticket.

Discovering patterns of activity in incident reports

5

Indicators across tickets
Indicators occur with diverse patterns across tickets, reporters and time. Time on x axis, count on y axis, color coded by reporter.
Malicious IP
Agency IP

US-CERT domain

Discovering patterns of activity in incident reports

6

Similarity of indicators
Ticket'1 time

A

E

D C

B

Beginning with a reference indicator, we find indicators similar to it.
Example: a malicious IP

� Colored circles are tickets
� Grey circles are indicators
� Large indicators near center of circle have similar occurrence patterns to the reference indicator.

Discovering patterns of activity in incident reports

7

Indicator communities

But what if we aren't starting with a reference indicator?
We assume that indicators generated by a coherent real world process will be more likely to co-occur in tickets than arbitrary pairs of indicators.
Find groups of highly similar indicators in complete indicatorticket graph.

Discovering patterns of activity in incident reports

8

Indicator-ticket graph

A subset of the ticket-indicator graph (for a small set of selected indicators)
� Tickets are grey triangles
� Indicators are black circles
� Edges connect tickets to the indicators they contain

Discovering patterns of activity in incident reports

9

Indicator-indicator weighted graph
Tickets are observations, focus on relationships between indicators.
Create a graph of indicators where the edge weight is determined by Jaccard similarity:

Where A and B are the sets of tickets containing Indicator A and Indicator B respectively.

Discovering patterns of activity in incident reports

10

Community detection
Community detection algorithms find groups of vertices that are interconnected

� MD5 � 3 phishing email addresses � Filename � File paths � IPs

� DHS domain � Email for submitting virus information � DHS informational website

Discovering patterns of activity in incident reports

11

Communities as objects
Each detected community has measurable characteristics � Connectivity � Number of reporters,
indicators, indicator types, tickets � Date ranges
Can find communities with particular characteristics, or communities similar to a reference community.

Discovering patterns of activity in incident reports

12

Integrating additional information

We matched indicators against blacklists.
(A) Can help interpret communities and sub-communities, or find interesting communities.
(B) Can supplement or correct blacklists.

Additional information could

� Supplement similarity metric IP

� Improve or tune community detection algorithm

� Tag or annotate

IP

communities

IP
IP IP IP IP

IP
email(and(domain of(malicious(activity zeroaccess(descriptive(page
malicious(domain(pattern( IP
IP

IP

IP

IP IP

Discovering patterns of activity in incident reports

13

Continuing work
1. Find `interesting' communities based on similarity to labeled examples.
2. Track evolution of a type of community over time. How do different types of communities develop?
3. Integrate expert information or additional data sources.
4. Explore value for predictive forecasting.

Discovering patterns of activity in incident reports

14

Summary
� We consider the tickets taken together as a sample of observations of coherent activities.
� We use statistical patterns in indicators across tickets and reporters to estimate similarity metrics and indicator communities.
� Communities can be more accessible, concise, and semantically coherent than large sets of individual indicators.
� This inferred structure can be integrated with additional information such as blacklists.
� Ongoing work will improve the integration of learned structure with additional information, forecasting, decision making

Discovering patterns of activity in incident reports

15

References
Network tie strength (similarity)
Gupte, M., & Eliassi-Rad, T. (2012). Measuring tie strength in implicit social networks. Proceedings of the 3rd Annual ACM Web Science Conference on - WebSci '12, 109�118. doi:10.1145/2380718.2380734
Community detection algorithm InfoMap M. Rosvall and C. T. Bergstrom, Maps of information flow reveal community structure in complex networks, PNAS 105, 1118 (2008)

Discovering patterns of activity in incident reports

16

