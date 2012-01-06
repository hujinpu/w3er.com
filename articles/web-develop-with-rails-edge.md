title: 基于rails新版本web开发经验分享
date: 2012-01-06

默认rails3.1.3不支持mongodb，需要一个新的orm framework，它就是[MongoMapper](http://mongomapper.com/) 。

可以这样启动一个新的rails项目： `rails new your_app_name --skip-active-record` ，这里的重点就是不要生成active-record的配置代码

同时，需要在your_app_name/config/initializers/mongo.rb 创建mongo.rb文件，内容为：

`MongoMapper.database = "your_database_name_prefix-#{Rails.env}"`

对于喜欢使用generator的同学，需要对于model代码的生成指定orm的名字，这里就是： `rails g scaffold blog title:string content:string --orm=mongo_mapper`

生成的对应代码为：

    class Blog
      include MongoMapper::Document

      key :title, String
      key :content, String

    end

注意：mongo_mapper默认支持的格式没有text，详情见[types](http://mongomapper.com/documentation/types.html)