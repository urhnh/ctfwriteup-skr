# Challenge

![challenge](https://github.com/urhnh/ctfwriteup/assets/149639198/cd853707-6ae4-459d-9fae-b39dcded88cc)

Hint: It is not as complicated as it seems..

# Solution

```
#!/usr/bin/env python3
p = input(" :edocssap eht retnE"[::-1]); print("}s%{RKS si galF !edocssap tcerroC"[::-1] % p if len(p) == 9 and p[1337^1337] == 'D' and p[1**1337] == '3' and p[len('2'*2)] == '4' and p[3] == p[len('')] and p[len('skrr')] == '-' and p[5] == 'B' and p[(len('6'*6)-5)*6] == p[1<<1337>>1337] and p[int(p[6])+4] == p[len(p)-3] and p[len(p[1:])] == 'F' else " ! e d o c s s a p   g n o r W"[::-1][::2])
```
It is python code. Try to execute it, we will see the spelling in the code is just written backward. Let's arrange the code to see it clearer,

```
p = input(" :edocssap eht retnE"[::-1]);
print("}s%{RKS si galF !edocssap tcerroC"[::-1] % p
  if len(p) == 9 and
      p[1337^1337] == 'D' and
      p[1**1337] == '3' and
      p[len('2'*2)] == '4' and
      p[3] == p[len('')] and
      p[len('skrr')] == '-' and p[5] == 'B' and
      p[(len('6'*6)-5)*6] == p[1<<1337>>1337] and
      p[int(p[6])+4] == p[len(p)-3] and
      p[len(p[1:])] == 'F'
  else " ! e d o c s s a p   g n o r W"[::-1][::2])
```

the correct passcode should have 

- 9 characters

- 1337^1337=0 so, p[0] is 'D'

- 1**1337=1 so, p[1] is '3'

- len('2'*2)=2 so, p[2] is '4'

- len('')=2 so, p[3] is '2'

- len('skrr')=4 so, p[4] is '-'

- p[5] is 'B'

- len('6'*6)-5)*6=6 and 1<<1337>>1337=1 so, p[6]=p[1]='3'

- int(p[6])+4=7 and len(p)-3=6 so, p[7]=p[6]='3'

- len(p[1:])=8 so, p[8]='F'

Will get the passcode 'D342-B33F'

(if you need further explanation, can try chatgpt. really helps!)


