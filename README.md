# 排火车
import random
import time
m = 0   #计算后手胜利次数
n = 0   #计算先手胜利次数
x = input("请输入测试次数：")  #由用户决定排火车的局数，当某一方手牌数为零时，游戏结束算作一局游戏
start = time.perf_counter()    #用于计算程序执行所花费的时间
for i in range(eval(x)):
    a = [1,2,3,4,5,6,7,8,9,10,11,12,13]    #a假设为先手
    a*=4
    b = []
    c = []
    z = 51
    s = 0
    for i in range(26):                    #从列表a中随机抽取26个数字到列表b中，即a、b分别为先手和后手
        d = random.randint(0,z)
        b.append(a.pop(d))
        z = z - 1
    while len(a) != 0 and len(b) != 0:
        c.append(a.pop(0))
        while c[-1] in c[:-1]:
            e = c.index(c[-1],0,-1)
            s = len(c) - c.index(c[-1],0,-1)
            for i in range(s):
                a.append(c.pop(e))
            random.shuffle(a)
            c.append(a.pop(0))
        c.append(b.pop(0))
        while c[-1] in c[:-1]:
            e = c.index(c[-1],0,-1)
            s = len(c) - c.index(c[-1],0,-1)
            for i in range(s):
                b.append(c.pop(e))
            random.shuffle(b)
            c.append(b.pop(0))
    else:
        if len(a) == 0:
            m = m + 1
        else:
            n = n + 1
end = time.perf_counter()
print("先手胜利{:}次；后手胜利{:}次".format(n,m))
print("计算用时{:.4f}秒".format(end - start))
