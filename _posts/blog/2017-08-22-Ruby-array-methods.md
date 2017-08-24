---
layout: post
title: Ruby中数组方法
categories: Ruby
description: Ruby中数组方法
keywords: ruby,array
---
Ruby数组方法

<hr>
<table border = "2">  
	 <caption>Ruby数组方法</caption>
	<tr>
		<th>函数名称</th>
		<th>说明</th>
		<th>示例</th>
	</tr>
	<tr>
		<td align = "center"> & </td>
		<td>与运算，返回两数组的交集</td>
		<td>[1,2] & [2.3]  => [2]</td>
	</tr>
	<tr>
		<td align = "center"> * </td>
		<td>复制数组n次，返回新数组</td>
		<td>[1,2] * 2 => [1,2,1,2]</td>
	</tr>
	<tr>
		<td align = "center"> + </td>
		<td>返回两数组的并集，但不排除重复元素</td>
		<td>[1,2] + [2,3] => [1,2,2,3]</td>
	</tr>
	<tr>
		<td align = "center"> << </td>
		<td>追加元素，但不排除重复元素</td>
		<td>[1,2] << [2,3] => [1,2,2,3]</td>
	</tr>
	<tr>
		<td align = "center"> |</td>
		<td>追加元素，但排除重复元素</td>
		<td>[1,2] | [2,3] => [1,2,3]</td>
	</tr>
	<tr>
		<td align = "center"> - </td>
		<td>返回第一个数组和第二个数组不同的元素</td>
		<td>[1,2] - [2,3] => [1]</td>
	</tr>
	<tr>
		<td align = "center"> <=> </td>
		<td>如果数组a小于、等于或大于数组b，则返回一个整数（-1、 0 或 +1）</td>
		<td>[1,2] | [2,3] => -1</td>
	</tr>
</table>