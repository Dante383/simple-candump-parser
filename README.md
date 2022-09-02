# Simple candump parser

This is a very simple script made to parse candump logs. It'll count each id's occurencies, calculate average time between them
and list all possible values for each data slot. It was written in twenty-something minutes because I needed a quick solution. 
It is not flexible, it's not optimal, it's not perfect - but it helped me, so I hope it can help someone else too.

## Usage 

First, you'll need a candump log in a format likes this:

`(1367859965.231495) can0 440#4000800000000000
(1367859965.249499) can0 442#4200800000000000
(1367859965.330495) can0 440#4001800000000000
(1367859965.335500) can0 620#1080000000400080
(1367859965.349499) can0 442#4201800000000000`

You can achieve it by running `candump -l can0,0:0,#FFFFFFFF`

Then run the script.

`python simple-candump-parser.py candump-name-of-your-file.log`

The output will look something like this:

```
CAN ID: 4B8
    Occurencies: 2
    Average time between occurencies: 500ms
    Possible values:
        Data 1: 00,11
        Data 2: 00,7E
        Data 3: 00
        Data 4: 00,6B
        Data 5: 00,74
        Data 6: 00,3D
        Data 7: 00,8A
        Data 8: 00,62
 
 
 
CAN ID: 2F0
    Occurencies: 14
    Average time between occurencies: 65ms
    Possible values:
        Data 1: 00
        Data 2: 00
        Data 3: 00
        Data 4: F6
        Data 5: 
        Data 6: 
        Data 7: 
        Data 8: 
 
 
 
CAN ID: 61A
    Occurencies: 1
    Possible values:
        Data 1: 24
        Data 2: 80
        Data 3: 00
        Data 4: 00
        Data 5: 00
        Data 6: 00
        Data 7: 34
        Data 8: 40
 
 
 
CAN ID: 61C
    Occurencies: 1
    Possible values:
        Data 1: 26
        Data 2: 80
        Data 3: 00
        Data 4: 00
        Data 5: 00
        Data 6: 00
        Data 7: 00
        Data 8: 00
 
 
 
CAN ID: 024
    Occurencies: 70
    Average time between occurencies: 12ms
    Possible values:
        Data 1: 51
        Data 2: FE,FF,EF,C2,84,5F,53,4F,4E,65,BB,E9,F7,FC
        Data 3: 0A,08,09,02
        Data 4: 0B,0C,0A,67,E5,E7,B4,F3,08
        Data 5: 49,4B,4A,41
        Data 6: FC,FB,FD,6A,99,1A,1F,4C,12,FE,FA,F9
        Data 7: 80
        Data 8: 55,56,54,53,1F,4E,4F,44,16,DA,B4,A8,A3,92,91,AA,00,2E,3C,41,42,43

```

If you want, you can also get json output by adding 'json' after the filename, like so:

`python simple-candump-parser.py candump-name-of-your-file.log json`