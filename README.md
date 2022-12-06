# ticketmaster-discovery-client
---
***This is the refactored code for stps 1-2 of my Ticketmaster Discovery Client which is used in my [Tableau Dashboard](https://public.tableau.com/shared/9GB475ZQY?:display_count=n&:origin=viz_share_link).***
### Purpose:
This client provides an interface for retrieving all events from Ticketmaster for a list of states and a range of dates. 

### Considerations:
The API only allows access to 1000 elements in a single API call. This is determined by `page count` x `page size` = 1000 and `Page size` is capped at 200.

Accessing one page counts as an API call. To maximize the number of events retreived per API call, I used the maximum page size allowed. 
This way only 5 API calls are needed to access 1000 events. 

Because events came with complete embedded venue and attraction information, and attraction and venue information did not contain embedded events, I chose to focus my efforts on extracting events since all information could be pulled from this.

Through testing, I found that the more populus states had up to 900 events in a single day. This is close to but less than the 1000 element limit.

The code is broken into three phases all which save out .csv files. 
### Phase 1: Get event json files.
This step saves unflatted json files as .csv files.
### Phase 2: Flatten & Expand jsons
This step saves a csv with desired information extracted and flattened. Events are duplicated when there are multiple attractions. For example a NBA game will have two records, one for each teamm playing.
### To Do: Phase 3: Combine all files into one csv.
### To Do: Phase 4: Wrangle data and combine with master events database.
