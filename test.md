**https://blog.csdn.net/duan19920101/article/details/50617190/**

**vector中insert()的用法详解：http://blog.csdn.net/duan19920101/article/details/51557854**

---


**1.介绍**

在c++中，vector是一个十分有用的容器。

作用：它能够像容器一样存放各种类型的对象，简单地说，vector是一个能够存放任意类型的动态数组，能够增加和压缩数据。

vector在C++标准模板库中的部分内容，它是一个多功能的，能够操作多种数据结构和算法的模板类和函数库。


特别注意：

使用vector需要注意以下几点：

1、如果你要表示的向量长度较长（需要为向量内部保存很多数），容易导致内存泄漏，而且效率会很低；

2、Vector作为函数的参数或者返回值时，需要注意它的写法：

   double Distance(vector<int>&a, vector<int>&b) 其中的“&”绝对不能少！！！


实例：vector<int>test;

//建立一个vector，int为数组元素的数据类型，test为动态数组名

简单的使用方法如下：

vector<int>test;//建立一个vector

test.push_back(1);

test.push_back(2);//把1和2压入vector，这样test[0]就是1,test[1]就是2

 

自己见到的实例：

vector<vector<Point2f> > points; //定义一个二维数组

points[0].size();  //指第一行的列数

1 、基本操作

(1)头文件#include<vector>.

(2)创建vector对象，vector<int> vec;

(3)尾部插入数字：vec.push_back(a);

(4)使用下标访问元素，cout<<vec[0]<<endl;记住下标是从0开始的。

(5)使用迭代器访问元素.

vector<int>::iterator it;

for(it=vec.begin();it!=vec.end();it++)
 
> cout<<*it<<endl;

(6)插入元素：    vec.insert(vec.begin()+i,a);在第i+1个元素前面插入a;

(7)删除元素：    vec.erase(vec.begin()+2);删除第3个元素

vec.erase(vec.begin()+i,vec.end()+j);删除区间[i,j-1];区间从0开始

(8)向量大小:vec.size();

(9)清空:vec.clear();

特别提示：这里有begin()与end()函数、front()与back()的差别

**2、算法**

(1) 使用reverse将元素翻转：需要头文件#include<algorithm>

reverse(vec.begin(),vec.end());将元素翻转，即逆序排列！

(在vector中，如果一个函数中需要两个迭代器，一般后一个都不包含)

(2)使用sort排序：需要头文件#include<algorithm>，

sort(vec.begin(),vec.end());(默认是按升序排列,即从小到大).

可以通过重写排序比较函数按照降序比较，如下：

定义排序比较函数：

bool Comp(const int &a,const int &b)
{
    return a>b;
}
调用时:sort(vec.begin(),vec.end(),Comp)，这样就降序排序。 

**3.输出Vector的中的元素**

vector<float> vecClass; 

int nSize = vecClass.size();   

>  //打印vecClass,方法一：  
>  for(int i=0;i<nSize;i++)  
> {  
>    cout<<vecClass[i]<<"     ";  
> }  
>    cout<<endl; 

**需要注意的是：以方法一进行输出时，数组的下表必须保证是整数。**

>  //打印vecClass,方法二：     
> for(int i=0;i<nSize;i++)  
> {  
>    cout<<vecClass.at(i)<<"     ";  
> }  
>    cout<<endl;  
   
> //打印vecClass,方法三：输出某一指定的数值时不方便
> for(vector<float>::iterator it = vecClass.begin();it!=vecClass.end();it++)  
> {  
>     cout<<*it<<"   ";  
> }  
>     cout<<endl;  

**4.二维数组**
> #include "stdafx.h
> 
> #include <cv.h>
> 
> #include <vector>
> 
> #include <iostream>
> 
> using namespace std;
> 
> 
> int main()
> 
> {
> 	using namespace std;
> 
> 	int out[3][2] = {1,2,3,4,5,6};
>
> 	vector <int*> v1;
> 	
> 	v1.push_back(out[0]);
>
> 	v1.push_back(out[1]);
>
> 	v1.push_back(out[2]);
>  
> 	cout << v1[0][0] << endl;//1
>
> 	cout << v1[0][1] << endl;//2
>
> 	cout << v1[1][0] << endl;//3
>
> 	cout << v1[1][1] << endl;//4
>
> 	cout << v1[2][0] << endl;//5
>
> 	cout << v1[2][1] << endl;//6
>  
> 	return 0;
> }
