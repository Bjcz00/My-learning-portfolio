# The Stolen Sound

### Initial Case Information

They have given the following text prior to starting to us:"In the neon glow of 1980s Los Angeles, the West Hollywood Records store was rocked by a daring theft. A prized vinyl record, worth over $10,000, vanished during a busy evening, leaving the store owner desperate for answers. Vaguely recalling the details, you know the incident occurred on July 15, 1983, at this famous store. Your task is to track down the thief and bring them to justice.".
You can notice a few keypoints from this:
| Category | Information |
|---|---|
| Time | Evening of July 15th, 1983 |
| Missing Item | A prized vinyl record, worth over $10,000 |
| Location |  the West Hollywood Records store in Los Angeles |


### Investigation Objectives
**1.** Retrieve the crime scene report for the record theft using the known date and location.
    
**2.** Retrieve witness records linked to that crime scene to obtain their clues.
    
**3.** Use the clues from the witnesses to find the suspect in the suspects table.
    
**4.** Retrieve the suspect's interview transcript to confirm the confession.


# Investigation Process

## Step 1 - Retrieve the Crime Scene Report

My first step was checking what I already had, and I noticed one of the things I had was a very specific date. July 15th, 1983. Considering this is in LA I decided to write it in the way Americans write the date 19830715.

### SQL Query:
**SELECT * FROM from crime_scene WHERE date=19830715**

I also could've added AND Location="West Hollywood Records", but this gives the same result.

### Result:
| ID | Date | Type | Location | Description |
|---|---|---|---|---|
| 65 | 19830715 | theft | West Hollywood Records | A prized vinyl record was stolen from the store during a busy evening. |

### Finding:
This result didn't really reveal that much that we didn't already know, however, it did give us an ID for the crime, "65" to be exact.

## Step 2 - Retrieving Witness Records
The only new thing I got from the previous query was the ID "65". So, I'm quite sure this is our key for the next clue. We are going to use this to find the clues.

### SQL Query:
**SELECT * FROM witnesses WHERE crime_scene_id=65**

### Result:
Doing this gives us two extra clue reveals from witness statements:
| ID | Crime Scene ID | Clue |
| --- | --- | --- |
| 28 | 65 | I saw a man wearing a red bandana rushing out of the store. |
| 75 | 65 | The main thing I remember is that he had a distinctive gold watch on his wrist. |

### Finding:
From this we got two clues about the physical appearance. The thief was wearing a *red* bandana as well as a *gold watch*.

## Step 3 - Find the Suspect
With these steps I'm able to filter my suspect list down to 3 people.

### SQL Query:
**SELECT * from suspects WHERE accessory="gold watch" AND bandana_color="red"**

### Result:
| ID | Name | Bandana Color | Accessory |
|---|---|---|---|
| 35 | Tony Ramirez | red | gold watch |
| 44 | Mickey Rivera | red | gold watch |
| 97 | Rico Delgado | red | gold watch |

### Finding:
Based on this result we got 3 different individuals now that can be the thief: Tony Ramirez (ID: 35), Mickey Rivera (ID: 44), Rico Delgado (ID: 97)

## Step 4 - Retrieve Suspect's confessions
For this, we can just search them by their ID, that we found in our previous search.

### SQL Query: 
**SELECT * FROM interviews WHERE suspect_id=35 OR suspect_ID=44 OR suspect_ID=97**

I decided to use OR here so it would show an overview of all the results I want.

### Result:
| Suspect ID | Transcript |
| --- | --- |
| 35 | I wasn't anywhere near West Hollywood Records that night. |
| 44 | I was busy with my music career; I have nothing to do with this theft. | 
| 97 | I couldn't help it. I snapped and took the record. |

# Final Conclusion
As we can tell by the confession the thief was suspect number 97, A/K/A Rico Delgado. This ended up thankfully being quite an easy to go through challenge as it was all very self-explaining.

