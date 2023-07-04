# bigsender
name = input("Enter file:")
if len(name) < 1:
    name = "mbox-short.txt"
handle = open(name)

lst = list()

for line in handle:
    if not line.startswith("From:"): 
        continue
        
    linelst = line.split()
    lst.append(linelst[1]) 

counts = dict()
for word in lst:
    counts[word] = counts.get(word,0) + 1

bigcount = None
bigword = None
for word,count in counts.items(): 
    if bigcount is None or count > bigcount:
        bigcount = count
        bigword = word

print (bigword,bigcount)
