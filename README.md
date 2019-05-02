# Assigment-4
Assignment 4 Python
Define the sequence unique
1
def kmers(seq):
2
    sequence = seq
3
    seq_len = len(sequence)
4
    pos = []
5
    uni_l = []
6
    lin_clx = []
7
    counter = 0
8
    print('Sequence entered: ',sequence)
9
    print('Sequence length (kmax):',seq_len)
10
    for k in range(1,10):
11
        counter = counter+1
12
        for i in range(seq_len-k+1):
13
            trial=sequence[i:k]
14
            if i==0:
15
                t=k
16
                kobs=[]
17
                kobs.append(trial)
18
            else:
19
                p=0
20
                for j in range(len(kobs)):
21
                    if kobs[j] == trial:
22
                        p=1
23
                    else:
24
                        p=p
25
                if p==0:
26
                    kobs.append(trial)
27
            k=k+1
28
               
29
            if i==0:
30
                kpos = 0
31
                if seq_len-t+1>4**t:
32
                    kpos = 4**t
33
                    pos.append(kpos)
34
                else:
35
                    kpos = seq_len-t+1
36
                    pos.append(kpos)
37
        unicount = len(kobs)
38
        uni_l.append(unicount)
39
        lc = unicount/kpos
40
        lin_clx.append(lc)
41
        print('Observed kmers in kmer =',counter,'is ',kobs)
42
    lc2 = sum(uni_l)/sum(pos) 
43
    
44
    #print('Linguistic Complexity for each kmer; at kmer',seq_len,'kmers :',lin_clx)
45
    print('Linguistic Complexity (total) = ',lc2)
46
    print('Possible kmers amount for',seq_len,'kmers :',pos)
47
    print('Observed kmers amount for',seq_len,'kmers :',uni_l)
48
    print('Plotting possible kmers vs. kmers')
49
​
50
    #before plotting the function, we should define the range of kmers
51
    k = range(1,10)
52
    import matplotlib.pyplot as plt
53
    plt.plot (k,pos)
54
    plt.ylabel ('possible')
55
    plt.xlabel ('kmers')
56
    plt.title ('kmers proportion')
57
    
58
    #import pandas as pd for make a table
59
    import pandas as pd
60
    df = pd.DataFrame({'possible kmers':pos})
61
    df = pd.DataFrame({'observed kmers':uni_l})
62
    df.index = range(1,10)
63
    df['possible kmers'] = pos
64
    return df
df = kmers('ATTTGGATT')

Readme
y = kmers('x')

where: y = output of pandas data frame of observed and possible kmers x = input of string format of sequence

1
​
