# ZX81-CodeGolf-HappyBirthday
Happy Birthday to Raffaele Cecco

I had my first go at 'code golf' recently based on the question posed at https://codegolf.stackexchange.com/questions/119793/happy-birthday-raffaele-cecco the basic aim of which was to animate a Happy Birthday message around a rectangle in as few bytes as possible.

My initial attempt took up a massive 158 bytes (compiled) but was a bit poor as I stored the birthday message twice and stepped through it using a simple offset index - this way I did not have to worry about complex pointer usage etc. The basic process was to write the characters across the top of the screen (starting with the first character in the message), then down the right of the screen, then across the bottom of the screen, stepping backwards throught the screen memory but forwards throught the message and then back up the left of the screen. I would then increase the start point of the message (thus needing it twice) by 1 and repeat after a small delay based on the frame rate of the zeddy. I would wait 10 frames or one fifth of a second.

I received several suggestions of how to decrease it slightly from various people but one in particular was very significant. 'kmurta' suggested animating the message directly rather than worrying about pointers or storing the string twice. After implementing this idea the size was reduced to 128 bytes! There are still a few bytes that can be saved but not too many now.

The new process is to write the characters across the top of the screen (starting with the first character in the message), then down the right of the screen, then across the bottom of the screen, stepping backwards throught the screen memory but forwards throught the message and then back up the left of the screen. 
I would then modify the message by pushing the first character onto the stack, moving all the characters down one and then popping the first character off the stack onto the last character position. This all then repeats after a small delay based on the frame rate of the zeddy as above.

I have included the .p file should you wish to run this in an emulator and the .lst showing the full Z80 including all the stuff required by the ZX81 in order to be able to run the program. The section of the .lst specific to my 128 bytes is from &407D to &40FF which includes the required line 1 (a REM to hold the machine code) and line 2 (a RAND USR to activate it).
The actual code itself is from &4082 to &40EF.

The code is pretty heavily commented so I have not addded any extra here. 
