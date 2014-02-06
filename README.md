Ov1
===
Oppgave 3

Why you need concurrency? 
Multithreading(MT) lar en pc :
Prosessoren kan deles opp, og kjører flere program på samme tid. 
F.eks: vi kan bruke spotify mens vi gjør øving.
Dersom man har fler prosessorer går ting mye raskere. Selv om en prosessor kan fungere på mange tråder går det raskere når det er fler 
Hvordan kan MT gjøre programmering lettere:
Vi trenger ikke tenke på at ting må gjøres i rekkefølge. Ting kan gjøres parallelt.  
Hvordan kan MT gjøre programmering vanskligere: 
Man kan få tull med delte variabler dersom flere tråder jobber med samme verdi samtidig. 

Process
En prosess eier egne resurser som får tildelt egne rersusser av OP(har fast mengde), og deler ikke adress space eller fil resurser med mindre man implemeterer arv eller delt minne. 
Threads
Tråder deler minne,og filressurser og eier ingen i motsetning til en prosess. 
Operativsystemet tar seg av trådhåndtering. 
Green threads
I stedet for at et oprativsystem tar seg av tråd håndtering gjør en annen komponent dette. Denne kalles Virtual Machine.(VM) 
Fibers
Fiber klarer bare å kjøre et fiber om gangen,og må tillate at et nytt fiber overtar arbeidet,imotsetning til tråder.  
Deler adress spaces
threading.thread()

pthread_creat()
Lager en ny tråd

Go
green threads


Hvordan fungerer (denne låsen) “Pythin Global Interpreter Lock(GIL)” på en Python tråd. 
Den gjør det umulig for et Python prgram å multitaske,med mindre man spesifikt implementerer f.eks tråder. 
Man kan implementere: Må kjøre fler interpreter samtidig. 

func GOMAXPROCS(N int)
Denne funksjonen endrer antall CPUer som kan utføre operasjoner samtidig. 




Oppgave 4
Python: her får vi ut masse random tall i stigende rekkefølge. Slutttall er 1000000
why: Det er to tråder i programmet. Den ene tråden legger til i++, hele veien fra til 1 mill. Den andre tråden printer ut i, og denne vil hente i “random” i forhold til tråd 1. Derfor vil Den printe ut random tall og så vil den komme fra til neste print(når den går ut av for-løkken) og printe den siste i’en. 

Nå med to tråder: Vi får stigende tall og de er ikke veldig forskjellig før vi får done. Done tallet er riktig. 

kjøre: Python Test.py

C: En tråd: Det høyeste tallet vi fikk her var 40000,mens i Python var det 400000. Kan dette ha noe med at trådene kjøres mer parallellt???? Ender opp med rett tall.

Nå med to tråder: HEEEELT random. -8000<tall<30000. Done: -2147458682.Starter ikke på 0. Ble mindre random done svar enn i Go. t1 vil kjøre først. Leser i fra minne, legger til 1 så i=1. Nå starter t2 og leser i fra minne, den er 0. Trekker fra 1 i=-1. Lagrer i nå i minne. (I=-1). Kjører nå t1 og skriver i tilbake til minne(i=1). Får random tall som svar.

How to run a file in linux : ./FILENAME Husk å være inne i riktig mappe og lage filen først.

GO: en tråd: Det høyeste tallet vi fikk var 58000. Ender opp med rett tall her også. 

Nå med to tråder:Starter på 0.helt random tall igjen. ender på +-700000

Oppgave 6
programmet printer ut av linje 22 : 0,-1,4294967295,finner ikke det siste, men det skal vel være -4294967295?


4294967295 = 2^32 -1, og det gir mening at vi får dette som positivt og negativt tall i og med at long er 64bit .

long tar to oprasjoner: derfor 64. i vil derfor bli sett som 2^32. 
