正则替换例子
_imageCompressed.total() * _imageCompressed.elemSize() +    替换成  _imageCompressed.total() * MatElemSize(_imageCompressed) +


查找正则：  (\* _){1}(.+)(.elemSize\(\)){1}
解释：
 (\* _){1} 匹配 '* _' 开头的出现1次的  *要\转义
 (.+)中间任意串，长度不为0的    .+是大于0次的   .*是大于等于0次的
 (.elemSize\(\)){1}  匹配 '.elemSize()'出现1次的  后面()用 转义，所以是  \(\)  


notepad替换用 \1  \2 \3 ...   \2 代表 (.+)  第二个小括号里的内容     这里和正则关键字重复的字符需要转义  如()  这里变成  \(   _\2   \)
* MatElemSize\(_\2\)       


visual studio 替换用 $1 $2 $3 ...  $2 代表 (.+)  第二个小括号里的内容  这里和正则关键字重复的字符不需要转义 如()  这里还是 (   _$2  )
* MatElemSize(_$2) 