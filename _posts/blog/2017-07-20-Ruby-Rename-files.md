---
layout: post
title: Ruby批量重命名文件
categories: Ruby
description: 批量处理文件名
keywords: 脚本，批处理
---

##其实我是为了试试用markdown的感觉，附带改掉前几天贴的难看的代码
```ruby
# 思路：
# => A.遍历目录对象
# => B.获取目录下的文件名称File对象
# => C.判断文件后缀格式
# => D.截取新的文件命名
# => E.重命名
require 'find'
require 'pathname'
require 'fileutils'

puts "#####################开始脚本处理#######################"
puts "########################################################"
DIR_PHOTOS = "/Users/gongyangbo/projects/rubycode/photos_handle"
i = 0 #定义变量记录所有的符合规定格式的文件数量
j = 0 #记录被处理过的文件数量

Find.find(DIR_PHOTOS) do |filename| 
	path = Pathname.new(filename)
	extname = path.extname		# 文件后缀名
	begin
  		if extname == ".JPG" || extname == ".png" || extname == ".jpg" || extname == ".jpeg" || extname == ".PNG"
  			i = i + 1
		  	primary_name = path.basename		# 文件名
		  	if extname == ".jpeg"
		  		new_name = primary_name.to_s[-11..-1]		# 截取新的文件名
		  	elsif extname == ".JPG"
		  		new_name = primary_name.to_s[-10..-4] + "jpg"
		  	elsif extname == ".PNG"
		  		new_name = primary_name.to_s[-10..-4] + "png"
		  	else
		  		new_name = primary_name.to_s[-10..-1]
		  	end
		  	puts "-------------第#{i}张照片原名为:  #{primary_name}"
		  	if new_name.include?("+")
		  		puts "	\033[31m #{primary_name}格式不对,不做修改 \031"
		  	else
		  		j = j + 1
		  		File.rename(filename,new_name)
		  		puts "\033[36m----------------将被重命名为:  #{new_name}\033[0m\n"
		  	end
		  	puts "   \033[34mnext..\033[0m"
		  	puts ""
	  	end
	rescue Exception => e
  	
	end
end
puts "一共有 #{i} 张照片"
puts "本次处理了 #{j} 张照片"
```

![运行效果](http://upload-images.jianshu.io/upload_images/4755434-3e093b09fbc9318b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
