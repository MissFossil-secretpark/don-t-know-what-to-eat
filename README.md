# don-t-know-what-to-eat
a small but interesting programme

#请独立完成这个产品吧，我相信你可以的！
#刚进入产品时要做一个选择，在两个主要原因中选一个。
#当完全不知道要吃什么时，需要产品在一些菜品当众随机推荐一个，让我们选要或不要。
#当在几家店之间犹豫时，需要告诉电脑是哪几家，然后让电脑推荐一家，我们来做决策。这种情况要先输入再推荐，可以分别创建两个方法。

import random
import time


class dishmanager:
    reslist=[] 

    def recommend(self):#第一种，随机推荐美食
        while True:
            food=['馄饨','麻辣烫','香锅','凉皮','韩国火锅','串串','湘菜']
            a=random.choice(food)
            print('吃%s怎么样？'%a)
            confirm=input('接受推荐请输入y,继续推荐请按回车哦~\n')
            if confirm=='y':
                print('去吃%s，就这么愉快地决定了！'%a)
                break

    def hesitate(self):#第二种，让用户输入店名
        while True:
            resname=input('请告诉我您纠结的饭店名\n一家一家输哦，不再添加请输入n。输完请按回车：\n')
            if resname!='n':#防止把n也算进去
                self.reslist.append(resname)
            else:             
                print('------------小程序推荐中哦~------------')
                time.sleep(1)
                break

    def accept(self):   #第二种，在用户输入的店名中推荐
        while True:
            b=random.choice(self.reslist)
            print('去%s吃怎么样？'%b)
            confirm=input('接受推荐请输入y,继续推荐请按回车哦~\n')
            if confirm=='y':
                print('去吃%s，就这么愉快地决定了！'%b)
                break       
 
    def error(self):
        print('只能输入1或2呢，请重新输入哦')

    
    def menu(self):        
        print('欢迎使用今天吃什么小程序！')
        while True:
            ch=int(input('请选择您的需求：\n1.让小程序随便推荐点吃的...\n2.在几家店里犹豫，帮我做个决定吧\n'))                                    
            if ch==1:
                self.recommend()
                break
                                
            elif ch==2:
                self.hesitate()
                self.accept()
                break
            else:
                self.error()

        print('感谢使用今天吃什么小程序，用餐愉快哦！')  

chihuo=dishmanager()
chihuo.menu()

