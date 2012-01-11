title: 测试三十三
date: 2012-01-11

sadfasdfsadasdf

asdfasdfsa

asdfasdf

同时，需要在your_app_name/config/initializers/mongo.rb 创建mongo.rb文件，内容为：

`MongoMapper.database = "your_database_name_prefix-#{Rails.env}"`

在Gemfile里添加：

    gem 'mongo_mapper'
    gem 'bson_ext'

然后 `bundle install`
