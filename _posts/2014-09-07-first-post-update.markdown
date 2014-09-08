---
title: Hello,World!!
layout: post
tags:
    - lala
---

### 图片
1. 内链图片
<img src="/assets/images/2014/09/01/sysl.jpg" alt="小树">
--------------
2. 外链图片
![野田妹子](http://shane-pic.qiniudn.com/210e8a510fb30f24f830190bc895d143ac4b0393.jpg)


### 代码高亮
一段关于RakeFile的小程序：

    task :default => :generate

    desc 'Create new post with rake "post[post-name]"'
    task :post, [:title] do |t, args|
      if args.title then
        new_post(args.title)
      else
        puts 'rake "post[post-name]"'
      end
    end

    desc 'Build site with Jekyll'
    task :generate => :clean do
      `jekyll`
    end

    desc 'Start server'
    task :server => :clean do
      `jekyll --server`
    end

    desc 'Deploy with rake "depoly[comment]"'
    task :deploy, [:comment] => :generate do |t, args|
      if args.comment then
        `git commit . -m '#{args.comment}' && git push`
      else
        `git commit . -m 'new deployment' && git push`
      end
    end

    desc 'Clean up'
    task :clean do
      `rm -rf _site`
    end

    def new_post(title)
      time = Time.now
      filename = "_posts/" + time.strftime("%Y-%m-%d-") + title + '.markdown'
      if File.exists? filename then
        puts "Post already exists: #{filename}"
        return
      end
      uuid = `uuidgen | tr "[:upper:]" "[:lower:]" | tr -d "\n"`
      File.open(filename, "wb") do |f|
        f << <<-EOS
    ---
    title: #{title}
    layout: post
    guid: urn:uuid:#{uuid}
    tags:
      - 
    ---

    EOS
      %x[echo "#{filename}" | pbcopy]
      end
      puts "created #{filename}"
      `git add #{filename}`
    end


### gist
* 方式1
<script src="https://gist.github.com/abankowski/976117a254f49e039366.js"></script>
--------------
* 方式2
https://gist.github.com/976117a254f49e039366.git


### 引用
> 啦啦啦啦啦啦啦啦啦啦啦