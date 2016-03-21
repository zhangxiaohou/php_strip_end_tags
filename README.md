php strip_tags()无法只保留html结束标签

下例为只保留html结束标签的算法

```
\\传入的$content参数为已经用strip_tags()去除其他标签的字符串，如$content = strip_tags(“<p><b>ss</b></p>”);
function strip_end_tags($content){
  $content1 = "";
  $index = 0;
  for($i = 0;$i <= strlen($content);$i++){
    if($content[$i] != "<"){
    \\如果不是<标签，将这个字符放入结果字符串
      $content1 .= $content[$i];
    }else{
      if($content[$i+1] != "/"){
      \\如果找到<标签，且下一个不为"/"，索引跳到下一个>位置
        $i = strpos($content , ">" , $i);\\本行应该可以使用更加高效的方式
        $index = $i;
      }else{
        $content1 .= $content[$i];
      }
    }
  }
  return $content1;
}
```
