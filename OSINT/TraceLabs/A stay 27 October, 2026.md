# A stay (Easy)
Here we are going to look into one of the weekly OSINT challenges from TraceLabs, to start off this one is categorized as "Easy". The challenge goes like this:

An image recovered during a classified investigation provides a potential lead on a location of interest. Our task officers are on ground and we will share more as we get more Intel.
Your Task: identify the establishment and determine the exact room number from which the image was captured.
Flag Format: flag{XXXXXXXXXXXXXXNN}
Please DO NOT place any space or “” between the name of the Location.
Example flag{aplacesomewhere_20}

## Starting off
Okay, to start off, we received one image.

<img width="456" height="507" alt="image" src="https://github.com/user-attachments/assets/2109b38c-295e-4e45-8a22-e848e0eec65a" />

With this image, I ran a quick search through Google Images and it was quite fast to notice that this was the *Chateau Marmont* in *Los Angeles, California*

After a little more searching I noticed a YouTube video "https://www.youtube.com/watch?v=k7nQ4N0BhNc". This is a video uploaded by a person named David LaRue, where they showcase their room they booked in the hotel. The title of the video is " Room 79 at the Château Marmont July 12, 2021", the video starts off with a clip of the exact same location as the image.

## Result & Confirmation
This gave us the room number "Room 79". I went ahead to double check it to make sure I had the right place, and I noticed this site quite fast: http://www.simonbatters.com/room79.html.

Here it's also an image from the same view made from that exact room. So, I solved it. I went ahead and entered the final flag in TraceLabs' Discord flag{chateaumarmont_79} and it was correct :)
