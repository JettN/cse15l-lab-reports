# Lab Report 5

## Researching Commands

I decided to choose the `grep` command to research. I started by asking ChatGPT for some interesting ways to use the `grep` command.
My first interaction is pictured below.

![First ChapGPT Interaction](chatGPT_Grep.JPG)

I then asked ChapGPT for some more ways to use the `grep` command to see what other options there are.

![Second ChatGPT Interaction](chatGPT_Grep2.JPG)

From the 14 commands-line options for the `grep` command that ChatGPT gave me, I chose `-r`, `-v`, `-w`, and `-e`.
I also referenced [this website](https://man7.org/linux/man-pages/man1/grep.1.html) to understand the command-line options I chose better.
All of the examples below utilize the docsearch folder we used in lab report 3.

## `-r`

The option `-r` searches for the pattern recursively in all the files and directories under the specified directory.

```
$ grep -r -l Lucayans written_2/
written_2/travel_guides/berlitz2/Bahamas-History.txt
```

In the example above, I used the `-r` and `-l` options with `grep`. The `-l` option makes `grep` display only the file name of the file where the pattern is found.
The `-r` option allowed us to search all of the files and directories in `written_2/` for the pattern `Lucayans`. 
The `-r` option is useful if you need to search a directory to see if it contains a file with a pattern that you are looking for but do not know how many files are in the directory.

---

```
$ grep -r -l Lucayans written_2/non-fiction/

```

In the example above, I again used the `-r` and `-l` options with grep; however, I specified which subdirectory of `written_2/` to use `grep` on. 
This can be useful if you want to check if a specific subdirectory contains a pattern, potentially to bypass that subdirectory if it does not contain the pattern.

## `-v`

The option `-v` will display all the lines that do not match the specified pattern.

```
$ grep -v is written_2/travel_guides/berlitz2/Vallarta-History.txt

Puerto Vallarta
The village grew steadily, and by 1895 construction began on the church in the town center, 
Iglesia de Nuestra Señora de Guadalupe, named after the Virgin of Guadalupe, patron saint of the town. 
Sánchez originally founded the town on December 12th, the anniversary of the Virgin’s appearance.
As Las Peñas grew, San Sebastián faded. At its peak in the late 1800s, San Sebastián was one of the most 
productive mining towns in all Mexico, with a population of over 20,000 (today it has fewer than 2,000 residents). 
In 1912, governmental functions were moved to Las Peñas, and by 1819, Las Peñas was designated as a municipality, and its 
name changed to Puerto Vallarta.
Without any highways or an airport to connect it to other major cities, Puerto Vallarta remained in secluded tranquility 
for almost 50 years — until the 1963 filming of Night of the Iguana. 
The Hollywood production attracted the attention of the international media, 
who came looking for gossip about the torrid romances of the film’s legendary stars. 
Night of the Iguana’s biggest star, however, turned out to be the quaint village of Puerto Vallarta.
Manzanillo and the Costa Alegre
Acapulco: Colonial Gateway to the Orient and Playground to the Stars
Since those glory days Acapulco has aged — maybe not quite as gracefully as its fans would have hoped. 
However, the “Perla del Pacífico” still attracts scores of vacationers, who are still regaled by old stories 
about the rich and famous, told by seasoned waiters as they serve pool-side drinks with a weathered but unwavering smile.
Puerto Escondido and Huatulco
For centuries the bays of Huatulco basked quietly under the sun. 
hen, in the mid-1970s, FONATUR turned its eyes towards the southern coast of Oaxaca and started a mega-development, scheduled for completion in 2020, on the nine bays of Huatulco.
```

In the example above, I used the `-v` option with `grep` to search for lines in `Vallarta-History.txt` that do not contain the pattern "is". 
This is useful if you want to filter out sentences containing a certain word.

---

```
$ grep -v Cuba written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt

Where to Go
New Providence
It’s not the largest of the Bahamas islands and not the most stunningly beautiful, yet when most people think of the Bahamas they first think of New Providence or its major town, Nassau. The island is only 80 square miles in size yet 180,000 of the 280,000 Bahamians lives here. The town and its port and international airport are the hub for every activity in the Bahamas. Government, administration, taxes, and furniture shipments for new homes all start from here and radiate out to the other 
islands. New Providence also attracts over 3 million visitors every year, and Nassau is one of the main cruise ports of the 
Caribbean. The island is a magnet for fun seekers and serious shoppers, and it serves both very well.
Nassau
Nassau town has a fine pedigree dating back through colonial times, and the compact town center still has the feel of life under the English. Out in the natural harbor, which offered shelter to many a pirate ship, is a major port that can accommodate 15 large cruise ships at one time. This capacity was created in 1965 when public money was invested to dredge the port, specifically to allow bigger ships to enter. The huge vessels, hundreds of feet high, dwarf the towns buildings, which regulations set at a maximum of three stories, and create one of the most effective juxtapositions of modernity and history found 
anywhere in the world. The cruise port at Prince George Wharf brings in by far the majority of visitors to the Bahamas.     
Immediately in front of the cruise port you’ll find a line of horse-drawn surreys waiting to offer you a genteel tour along 
the historic streets. The horses wait under the cooling shade for their next customers. (In the hot summer months the horses are not allowed to work from 2–4pm.) The horses trot slowly past all the sights in town, but you can also easily stroll around yourself and see everything in a couple of hours — if you’re not seduced by the many shopping opportunities between the 
docks and the historic old town.
```

There was more text that printed when I ran the command in the example above but I did not include it because it was redundant.
In the example above, I used the `-v` option with `grep` to search for lines in `Bahamas-WhereToGo.txt` that do not contain the pattern "Cuba". 
In this particular example, the `-v` option is useful to exclude locations you do not want to visit, in this case Cuba. 
By using `-v`, you can save time by avoiding content in the travel guide that talks about Cuba since you do not want to go there.

## `-w`

The option `-w` matches only whole words instead of substrings.

```
$ grep -r -l cat written_2/travel_guides/berlitz2/
written_2/travel_guides/berlitz2/Algarve-History.txt
written_2/travel_guides/berlitz2/Algarve-Intro.txt
written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt
written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2/travel_guides/berlitz2/Amsterdam-History.txt
written_2/travel_guides/berlitz2/Amsterdam-Intro.txt
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt
written_2/travel_guides/berlitz2/Athens-History.txt
written_2/travel_guides/berlitz2/Athens-Intro.txt
written_2/travel_guides/berlitz2/Athens-WhatToDo.txt
written_2/travel_guides/berlitz2/Athens-WhereToGo.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Bali-History.txt
written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
written_2/travel_guides/berlitz2/Bali-WhereToGo.txt
written_2/travel_guides/berlitz2/Barcelona-History.txt
written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt
written_2/travel_guides/berlitz2/Barcelona-WhereToGo.txt
written_2/travel_guides/berlitz2/Beijing-History.txt
written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt
written_2/travel_guides/berlitz2/Beijing-WhereToGo.txt
written_2/travel_guides/berlitz2/Berlin-History.txt
written_2/travel_guides/berlitz2/Berlin-WhatToDo.txt
written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt
written_2/travel_guides/berlitz2/Bermuda-history.txt
written_2/travel_guides/berlitz2/Bermuda-WhatToDo.txt
written_2/travel_guides/berlitz2/Bermuda-WhereToGo.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/Budapest-WhatToDo.txt
written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt
written_2/travel_guides/berlitz2/California-History.txt
written_2/travel_guides/berlitz2/California-WhatToDo.txt
written_2/travel_guides/berlitz2/California-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-History.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/CanaryIslands-History.txt
written_2/travel_guides/berlitz2/CanaryIslands-WhatToDo.txt
written_2/travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
written_2/travel_guides/berlitz2/Cancun-History.txt
written_2/travel_guides/berlitz2/Cancun-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-WhereToGo.txt
written_2/travel_guides/berlitz2/China-History.txt
written_2/travel_guides/berlitz2/China-WhatToDo.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/Costa-History.txt
written_2/travel_guides/berlitz2/Costa-WhatToDo.txt
written_2/travel_guides/berlitz2/Costa-WhereToGo.txt
written_2/travel_guides/berlitz2/CostaBlanca-History.txt
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
written_2/travel_guides/berlitz2/Crete-History.txt
written_2/travel_guides/berlitz2/Crete-WhatToDo.txt
written_2/travel_guides/berlitz2/Crete-WhereToGo.txt
written_2/travel_guides/berlitz2/CstaBlanca-WhereToGo.txt
written_2/travel_guides/berlitz2/Cuba-History.txt
written_2/travel_guides/berlitz2/Cuba-WhatToDo.txt
written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt
written_2/travel_guides/berlitz2/Nepal-History.txt
written_2/travel_guides/berlitz2/Nepal-WhatToDo.txt
written_2/travel_guides/berlitz2/Nepal-WhereToGo.txt
written_2/travel_guides/berlitz2/NewOrleans-History.txt
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
written_2/travel_guides/berlitz2/Poland-History.txt
written_2/travel_guides/berlitz2/Poland-WhatToDo.txt
written_2/travel_guides/berlitz2/Portugal-History.txt
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2/travel_guides/berlitz2/PuertoRico-History.txt
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-History.txt
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```

```
$ grep -r -l -w "cat" written_2/travel_guides/berlitz2/
written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt
```

In the example above, I used the `-w` option to search for files in the `written_2/travel_guides/berlitz2/` directory for the word "cat".
This option is very useful if you are looking for lines or files (using the `-l`) containing specific words. 
In this case, the `-w` option was able to shorten the list of 78 files `grep` gave me down to 3 after specifying that I was only looking for the word "cat", rather than a substring containing "cat".

```
$ grep cat written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt 
Another majestic view of the city is from a charming park, Miradouro de Santa Luzia, just down the hill from the castle. 
Lisbon’s Sé Patriarcal (cathedral) appears out of nowhere at a bend in the road (most easily reached from the center by continuing east on the extension of Rua da Conceição). 
Begun as a fortress-church in the 12th century, its towers and walls suggest a beleaguered citadel. Adjacent to the cathedral is the lovely Igreja de Santo António da Sé, named for Lisbon’s patron saint, St. Anthony of Padua.
A wide pedestrian shopping street, Rua Augusta, leads from the Praça do Comércio through a stately arch to the 
central square of Lisbon, Praça Dom Pedro IV, better known as the Rossio (the Common). 
Once the scene of bullfights, it now hosts a funfair and is a popular meeting point, ringed by cafés. 
The National Theater is located here, and across the road is the Estação do Rossio (with trains to Sintra and other places), 
which looks something like a Moorish palace with horseshoe arches, just west of the square. 
Two blocks north is another lively square, Praça dos Restauradores, with its historic obelisk commemorating the overthrow of Spanish Hapsburg rule in 1640. The main tourist office is located here at Palácio Foz, on the west side of the square.
```
(There was more lines text produced by the `grep` command above that I did not include due to redundancy and space)

```
$ grep -w "cat" written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
Lagos was an important trading port under the Moors, but the town enjoyed its heyday after the Reconquest, when it was proclaimed the capital of the Algarve. 
On Rua General Alberta da Silveira, the tiny chapel Igreja de Santo António, an exuberant gilt Baroque work and one of the Algarve’s finest churches, 
was rebuilt soon after the earthquake. The entrance to the church is actually through the curious and eclectic museum next door, 
Museu Regional de Lagos. Rooms display sacred art, archaeological remains, the original charter of Lagos, holy vestments, and a bizarre collection of creatures, 
like a science experiment gone bad: an eight-legged goat kid preserved in formaldehyde, a one-eyed sheep, a cat with two faces.
```

