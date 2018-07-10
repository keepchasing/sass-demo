# sass 实践

## mixin定义

>   以下代码为mixin的定义，其中包含变量定义、引用以及if/else语法

>   Sass其他语法详见：[Sass中文网](https://www.sass.hk/docs/)

```
// 定义宽高固定button
@mixin button($width,$height,$fontSize:0,$borderRaduis:3)
{
	$fSize:0;
	@if $fontSize == 0 {	
		@if $height >= 36
		{
			$fSize:16;
		} @else if $height >= 28 and $height <36{
			$fSize:14;
		} @else if $height < 28{
			$fSize:12;
		}
	}@else{
		$fSize:#{$fontSize};
	}
    display: inline-block;
    width:#{$width}px;
    height:#{$height}px;
    line-height: #{$height}px;
    font-size: #{$fSize}px;
    border-radius: #{$borderRaduis}px;
}

// 定义宽度自适应、padding、font-size、border-raduis可传参button
@mixin adjustBtn($height,$padding:12,$fontSize:0,$borderRaduis:3)
{
	$fSize:0;
	@if $fontSize == 0 {	
		@if $height >= 36
		{
			$fSize:16;
		} @else if $height >= 28 and $height < 36{
			$fSize:14;
		} @else if $height < 28{
			$fSize:12;
		}
	}@else{
		$fSize:#{$fontSize};
	}
    display: inline-block;
    padding:0 #{$padding}px;
    height:#{$height}px;
    line-height: #{$height}px;
    font-size: #{$fSize}px;
    border-radius: #{$borderRaduis}px;
}
// 控制按钮高亮及空心实心
@mixin activeBtn($type:1){
	@if $type == 1{
		background-color: $color1;
		color:$color12;
		border:1px solid $color1;
	} @else if $type == 10{
		background-color: $color2;
		color:$color12;
		border:1px solid $color2;
	} @else if $type == 2{		
		color:$color1;
		border:1px solid $color1;
	} @else if $type == 20{
		background-color: $color1;
		color:$color12;
		border:1px solid $color1;
    }
    text-align: center;
	cursor: pointer;
}
// 按钮置灰
@mixin unactiveBtn(){
	background-color: $color10;
	color:$color12;
	border:1px solid $color10;
    text-align: center;
}


```

