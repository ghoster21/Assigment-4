# Assigment-4
## Assignment 4 Python
## Define the sequence unique
def kmers(seq):
    sequence = seq
    seq_len = len(sequence)
    pos = []
    uni_l = []
    lin_clx = []
    counter = 0
    print('Sequence entered: ',sequence)
    print('Sequence length (kmax):',seq_len)
    for k in range(1,10):
        counter = counter+1
        for i in range(seq_len-k+1):
            trial=sequence[i:k]
            if i==0:
                t=k
                kobs=[]
                kobs.append(trial)
            else:
                p=0
                for j in range(len(kobs)):
                    if kobs[j] == trial:
                        p=1
                    else:
                        p=p
                if p==0:
                    kobs.append(trial)
            k=k+1
            if i==0:
                kpos = 0
                if seq_len-t+1>4**t:
                    kpos = 4**t
                    pos.append(kpos)
                else:
                    kpos = seq_len-t+1
                    pos.append(kpos)
        unicount = len(kobs)
        uni_l.append(unicount)
        lc = unicount/kpos
        lin_clx.append(lc)
        print('Observed kmers in kmer =',counter,'is ',kobs)
    lc2 = sum(uni_l)/sum(pos) 
    
    #print('Linguistic Complexity for each kmer; at kmer',seq_len,'kmers :',lin_clx)
    print('Linguistic Complexity (total) = ',lc2)
    print('Possible kmers amount for',seq_len,'kmers :',pos)
    print('Observed kmers amount for',seq_len,'kmers :',uni_l)
    print('Plotting possible kmers vs. kmers')
    
    #before plotting the function, we should define the range of kmers
    k = range(1,10)
    import matplotlib.pyplot as plt
    plt.plot (k,pos)
    plt.ylabel ('possible')
    plt.xlabel ('kmers')
    plt.title ('kmers proportion')
    #import pandas as pd for make a table
    import pandas as pd
    df = pd.DataFrame({'possible kmers':pos})
    df = pd.DataFrame({'observed kmers':uni_l})
    df.index = range(1,10)
    df['possible kmers'] = pos
    return df
df = kmers('ATTTGGATT')

## Readme
y = kmers('x')

## where: y = output of pandas data frame of observed and possible kmers x = input of string format of sequence

                
