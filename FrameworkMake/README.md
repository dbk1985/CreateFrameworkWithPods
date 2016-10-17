# YWLib

[![CI Status](http://img.shields.io/travis/dlm/YWLib.svg?style=flat)](https://travis-ci.org/dlm/YWLib)
[![Version](https://img.shields.io/cocoapods/v/YWLib.svg?style=flat)](http://cocoapods.org/pods/YWLib)
[![License](https://img.shields.io/cocoapods/l/YWLib.svg?style=flat)](http://cocoapods.org/pods/YWLib)
[![Platform](https://img.shields.io/cocoapods/p/YWLib.svg?style=flat)](http://cocoapods.org/pods/YWLib)

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements

## Installation

YWLib is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "YWLib"
```

## Author

dlm, 376958755@qq.com

## License

YWLib is available under the MIT license. See the LICENSE file for more info.



1、创建一个目录（存放工程文件<类库功能，测试实例工程>）
	➜  C mkdir FrameworkMake
	➜  C pwd
		/Volumes/C
	➜  C cd FrameworkMake 
	➜  FrameworkMake pwd
		/Volumes/C/FrameworkMake
2、创建类库工程目录
	➜  FrameworkMake mkdir YWLib
	➜  FrameworkMake pwd
		/Volumes/C/FrameworkMake
	➜  FrameworkMake cd YWLib 
	➜  YWLib pwd
		/Volumes/C/FrameworkMake/YWLib

3、在类库目录下创建如下目录和文件
	➜  YWLib vim YWLib.podspec
	内容如下：
	#
	# Be sure to run `pod YWLib lint YWLib.podspec' to ensure this is a
	# valid spec before submitting.
	#
	# Any lines starting with a # are optional, but their use is encouraged
	# To learn more about a Podspec see http://guides.cocoapods.org/syntax/podspec.html
	#

	Pod::Spec.new do |s|
	  s.name             = 'YWLib'
	  s.version          = '0.1.0'
	  s.summary          = 'A short description of YWLib.'

	# This description is used to generate tags and improve search results.
	#   * Think: What does it do? Why did you write it? What is the focus?
	#   * Try to keep it short, snappy and to the point.
	#   * Write the description between the DESC delimiters below.
	#   * Finally, don't worry about the indent, CocoaPods strips it!

	  s.description      = <<-DESC
	TODO: Add long description of the pod here.
	                       DESC

	  s.homepage         = 'https://github.com/<GITHUB_USERNAME>/YWLib'
	  # s.screenshots     = 'www.example.com/screenshots_1', 'www.example.com/screenshots_2'
	  s.license          = { :type => 'MIT', :file => 'LICENSE' }
	  s.author           = { 'dlm' => '376958755@qq.com' }
	  s.source           = { :git => 'https://github.com/<GITHUB_USERNAME>/YWLib.git', :tag => s.version.to_s }
	  # s.social_media_url = 'https://twitter.com/<TWITTER_USERNAME>'

	  s.ios.deployment_target = '8.0'

	  s.source_files = 'YWLib/Classes/**/*'
	  
	   s.resource_bundles = {
	     'YWLib' => ['YWLib/Assets/*.png']
	   }

	   s.public_header_files = 'Pod/Classes/**/*.h'
	   s.frameworks = 'UIKit', 'MapKit'
	   s.dependency 'AFNetworking', '~> 2.3'
	   s.dependency 'Masonry'
	end

	// 工程原文件项目
	➜  YWLib mkdir YWLib
	➜  YWLib cd YWLib 
	➜  YWLib mkdir Assets
	➜  YWLib mkdir Classes

4、创建一个xproject工程
	FrameworkMake
	｜
	｜－－－－－ YWLib
				  |
				  |------YWLib.podspec
				  |------YWLib
				  		   |
				  		   |------- Assets
				  		   |------- Classes
	|--------- YWLib.xcworkspace
	|--------- Podfile
	|--------- LibDemo
				  |
				  |---------- LibDemo.xcodeproj
				  |---------- LibDemo工程文件
5、Podfile文件内容
	
	use_frameworks!
	project "./LibDemo/LibDemo.xproject"
	workspace "./YWLib.xcworkspace"
	target 'LibDemo' do
	  pod 'YWLib', :path => './YWLib'
	end

6、添加类库依赖的第三方类库，在podspec文件中添加，添加完成后使用pod install即可引入第三方类库



