# mid-term-exam
# encoding='utf-8'
with open("C:/Users/anjingdiandao/Desktop/1.txt") as f:
    lines= f.readlines()
    print(lines)
    t = [line.split() for line in lines]
    print (t)
#标题增加名次总分及平均分
title=t[0]
title.append('总分')
title.append('平均分')
title.insert(0,'名次')
#统计每个学生的总分及平均分后根据总分进行排序
tt=[]
for t1 in t[1:]:
    t2=[int(i) for i in t1[1:]]
    sumgrade = sum(t2)
    t1.append(str(sumgrade))
    t1.append(str('%.2f'%(sumgrade/9)))
    tt.append(t1)
ttnew=sorted(tt,key=lambda x:x[-2],reverse=True)
#汇总每一科目的平均分和总平均分
everygrade=[]
for n in range(1,12):
    sum = 0
    sum1 = 0
    for grade in ttnew:
        sum += float(grade[n])
        sum1 += 1
    everygrade.append("%.2f" %(sum/sum1))
everygrade.insert(0,"平均")
ttnew.insert(0,everygrade)
print(ttnew)
#替换不及格成绩为“不及格”,并添加名次
for x in range(1,len(ttnew)):
    for y in range(1,10):
        if float(ttnew[x][y]) < 60:
            ttnew[x][y] ='不及格'
ttnew = [['%d'%(ttnew.index(x))]+x for x in ttnew]
ttnew = [title] + ttnew
result = [' '.join(list)+'\n'for list in ttnew]
print(result)
with open('new_report.txt', 'w', encoding='utf8') as f:
    f.writelines(result)
