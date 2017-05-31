# JSON
### Json使用注意事项
* 首先使用json反序列化之前,应当在string字符串前面加上 **@** ,保证后面的字符串不进行转义,即忽略转义字符.在路径前也常用  
string b = @"c:\test" 和 string b = "c:\\test" 前者方便些  
但是用这种方法还是不能避免使用转义字符\" 转义双引号
* string.trim()删去字符串两边的空格换行等 string.trim(char c)删去两边的c字符
* 反序列化DeserializeObject对json字符串中的属性顺序不敏感
