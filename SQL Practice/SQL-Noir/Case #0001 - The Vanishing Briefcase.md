# The Vanishing Murders

### Initial Case information

There is one sentence given prior to doing anything, which is:"Set in the gritty 1980s, a valuable briefcase has disappeared from the Blue Note Lounge. A witness reported that a man in a trench coat was seen fleeing the scene. Investigate the crime scene, review the list of suspects, and examine interview transcripts to reveal the culprit."
You can notice a few key points from this:
| Category | Information |
|---|---|
| Time Period | Around 1980s |
| Missing Item | A valuable briefcase |
| Location | Blue Note Lounge |
| Description Potential Suspect | A man in a trench coat |


### Investigation Objectives
**1.** Retrieve the correct crime scene details to gather the key clue.

**2.** Identify the suspect whose profile matches the witness description.

**3.** Verify the suspect using their interview transcript.


# Investigation Process

## Step 1 - Retrieve Crime Scene Details

I started with what I already knew, the location. I started by searching for the crime scene record associated with that location.

### SQL Query:
**SELECT * FROM crime_scene WHERE location="Blue Note Lounge"**

### Result:
| ID | Date | Type | Location | Description
|---|---|---|---|---|
| 76 | 19851120 | Theft | Blue Note Lounge | A briefcase containing sensitive documents vanished. A witness reported a man in a trench coat with a scar on his left cheek fleeing the scene. |

### Finding:
This result gave another important thing about the suspect, besides further confirming the trench coat but besides that it revealed he has a *scar on his left cheek*. With these details we can narrow down the list.


## Step 2 - Matching the Suspects
With the results from the previous step I continued my search. I used both these results to look for a suspect with both of the qualities.

### SQL Query:
**SELECT * FROM suspects WHERE attire="trench coat" AND scar="left cheek"**

### Result:
| ID | Name | Attire | Scar
|---|---|---|---|
|3 | Frankie Lombardi | trench coat | left cheek |
| 183 | Vincent Malone | trench coat | left cheek |

### Finding:
The quary gave me two suspects that matched the description. Since both of them could be the suspect it requires more investigation.


## Step 3 - Watching the Interviews
The final step is looking through the interviews to tell who the suspect is. For this, I had to do 2 queries to check both the suspects with their ID.

### SQL Query 1:
**SELECT FROM interviews WHERE suspect_id=3**

### Result Query 1:
NULL. This means there was no interview transcript available for Frankie Lombardi.

### SQL Query 2:
**SELECT FROM interviews WHERE suspect_id=183**

### Result Query 2:
"I wasn't going to steal it, but I did."


# Final Conclusion
The identified suspect is **Vincent Malone**. He has admitted to being the person responsible for the theft.
This went better as I had expected as I've never used SQL prior to this. 
