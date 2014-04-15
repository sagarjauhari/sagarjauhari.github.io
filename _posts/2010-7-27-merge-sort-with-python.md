---
title: Merge Sort with Python
layout: post
category: code
tags: [algorithms python]
---

Here's a code for merge sort in Python. Drop in suggestions for a more
optimized code. ..\

~~~~
{style="font-family:arial;font-size:12px;border:1px dashed #CCCCCC;width:99%;height:auto;overflow:auto;background:#000000;;background-image:URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif);padding:0px;color:#f0f0f0;text-align:left;line-height:20px;"}
 def merge_sort(array):  
   if len(array)==1:  
     return array  
   elif len(array)==2:  
     if array[0]>array[1]:  
       return array  
     else:  
       return [array[1],array[0]]  
   else:  
     return merge(merge_sort(array[0:int(len(array)/2)]),merge_sort(array[int(len(array)/2):len(array)]))  
 def merge(array1,array2):  
   p1=0  
   p2=0  
   ans=[]  
   for i in range(len(array1)+len(array2)):  
     if p1!=len(array1) and p2!=len(array2):  
       if array1[p1]>array2[p2]:  
         ans.append(array1[p1])  
         p1=p1+1  
       else:  
         ans.append(array2[p2])  
         p2=p2+1  
     elif p1==len(array1):  
       ans.append(array2[p2])  
       p2=p2+1  
     elif p2==len(array2):  
       ans.append(array1[p1])  
       p1=p1+1  
   return ans  
~~~~
