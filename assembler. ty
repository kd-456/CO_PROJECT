import sys
import re
f=open("test.txt",'r')
f2=open("test_result.txt",'w')
input_list=[]
answer=[]
variables=[]
var_value=[]
labels=[]
labels_val=[]
opcode={'add':'00000','sub':'00001','mov1':'00010','mov2':'00011','ld':'00100','st':'00101',
        'mul':'00110','div':'00111','rs':'01000','ls':'01001','xor':'01010','or':'01011',
        'and':'01100','not':'01101','cmp':'01110','jmp':'01111','jlt':'11100','jgt':'11101',
        'je':'11111','hlt':'11010'}
register={'R0':'000','R1':'001','R2':'010','R3':'011','R4':'100','R5':'101','R6':'110','FLAGS':'111'}
register1={'R0':0,'R1':0,'R2':0,'R3':0,'R4':0,'R5':0,'R6':0}
flags = {'V': 0, 'L': 0, 'G': 0, 'E': 0}
stmtypes = {"add": "A", "sub": "A", "mov1": "B", "mov2": "C", "ld": "D", "st": "D", 
            "mul": "A", "div": "C", "rs": "B","ls": "B", "xor": "A", "or": "A",
             "and": "A", "not": "C", "cmp": "C", "jmp": "E", "jlt": "E", "jgt": "E",
             "je": "E", "hlt": "F",}

# for line in f:
#     input_list.append(line.strip().split(' '))
# lines=[]
for line in f:
    line =line.strip()
    if not  line:
        continue #remove whit e
    splt=[splt.strip() for splt in line.split()]
    input_list.append(splt)# splititng into variable ....
print(input_list)

def var_error(list):
    var_error=0
    if input_list[0][0]=='var':
        for i in range(1,len(input_list)):
            if input_list[i][0]=='var':
                if input_list[i-1][0]!='var':
                    var_error=1
                    return var_error
    else:
        var_error=1
        return var_error

for i in input_list:
    if i[0][-1]==':':
        labels.append(i[0][:-1]) 


    if i[0]=='mov':
        

        if (i[2][1]=='$'):
            register1[i[1]]=int(i[2][1:])
            answer.append(opcode['mov1'])

        else:
            answer.append(opcode['mov2'])
    if i[0] in opcode:
        answer.append(opcode[i[0]])
    if i[0]=='var':
        variables.append(i[1])
        counter=0
        bincounter=bin(counter)[2:]# removing 0b and bin for conversion 
        var_value.append("{0:07b}".format(len(variables)))
    if (i[-1])[-1]==':':
        labels.append(i[0][:-1])
        # f2.write(labels)
    if i[0][-1]==":":
        counter=0
        bincounter=bin(counter)[2:]# removing 0b and bin for conversion 
        # f2.write(bincounter)
        labels_val.append("{0:07b}".format(len(labels)))
