- 本文的两个教程皆建立在 #Linux 系统基础上
- #### GitLab社区版（CE）安装
	- 参考：[手把手教你搭建gitlab服务器](https://zhuanlan.zhihu.com/p/62042884)
	- 镜像链接：https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce
	- ubuntu: /ubuntu/pool/focal/main/g/gitlab-ce
		- 下载后在文件路径下执行
		- ```bash
		  sudo dpkg -i gitlab-ce-...x86_64.deb
		  ```
		- 编辑/etc/gitlab/gitlab.rb，更改GitLab URL下的external_url属性为服务器ip或域名，并设置端口，例：
		  `10.60.2.114:8081`
		- ```bash
		  gitlab-ctl reconfigure
		  gitlab-ctl restart
		  ```
		- 安装完成后会提示初始密码文件路径，复制密码并在刚刚配置的域名/ip访问gitlab，默认用户为root
- #### GitLab企业版（EE）安装
  id:: 630f148d-ea85-4142-9920-4b42bfdd49f3
	- 参考：[安装并破解Gitlab EE](https://blog.17lai.site/posts/29a820b3)，[Gitlab EE安装与破解](https://conf.top/post/506)
	- #### 安装GitLab
	  collapsed:: true
		- [Installation methods](https://docs.gitlab.com/ee/install/install_methods.html)
		- [gitlab官方镜像站](https://packages.gitlab.com/gitlab/gitlab-ee)
		- ```bash
		  curl gitlab-ee_VERSION.deb
		  dpkg -i gitlab-ee_VERSION.deb
		  ```
		- ```bash
		  sudo apt install ruby
		  gem install gitlab-license
		  vim license.rb
		  ```
		- license.rb
			- ```ruby
			  require "openssl"
			  require "gitlab/license"
			  key_pair = OpenSSL::PKey::RSA.generate(2048)
			  File.open("license_key", "w") { |f| f.write(key_pair.to_pem) }
			  public_key = key_pair.public_key
			  File.open("license_key.pub", "w") { |f| f.write(public_key.to_pem) }
			  private_key = OpenSSL::PKey::RSA.new File.read("license_key")
			  Gitlab::License.encryption_key = private_key
			  license = Gitlab::License.new
			  license.licensee = {
			    "Name" => "none",
			    "Company" => "none",
			    "Email" => "example@test.com",
			  }
			  license.starts_at = Date.new(2020, 1, 1) # 开始时间
			  license.expires_at = Date.new(2050, 1, 1) # 结束时间
			  license.notify_admins_at = Date.new(2049, 12, 1)
			  license.notify_users_at = Date.new(2049, 12, 1)
			  license.block_changes_at = Date.new(2050, 1, 1)
			  license.restrictions = {
			    active_user_count: 10000,
			  }
			  puts "License:"
			  puts license
			  data = license.export
			  puts "Exported license:"
			  puts data
			  File.open("GitLabBV.gitlab-license", "w") { |f| f.write(data) }
			  public_key = OpenSSL::PKey::RSA.new File.read("license_key.pub")
			  Gitlab::License.encryption_key = public_key
			  data = File.read("GitLabBV.gitlab-license")
			  $license = Gitlab::License.import(data)
			  puts "Imported license:"
			  puts $license
			  unless $license
			    raise "The license is invalid."
			  end
			  if $license.restricted?(:active_user_count)
			    active_user_count = 10000
			    if active_user_count > $license.restrictions[:active_user_count]
			      raise "The active user count exceeds the allowed amount!"
			    end
			  end
			  if $license.notify_admins?
			    puts "The license is due to expire on #{$license.expires_at}."
			  end
			  if $license.notify_users?
			    puts "The license is due to expire on #{$license.expires_at}."
			  end
			  module Gitlab
			    class GitAccess
			      def check(cmd, changes = nil)
			        if $license.block_changes?
			          return build_status_object(false, "License expired")
			        end
			      end
			    end
			  end
			  puts "This instance of GitLab Enterprise Edition is licensed to:"
			  $license.licensee.each do |key, value|
			    puts "#{key}: #{value}"
			  end
			  if $license.expired?
			    puts "The license expired on #{$license.expires_at}"
			  elsif $license.will_expire?
			    puts "The license will expire on #{$license.expires_at}"
			  else
			    puts "The license will never expire."
			  end
			  ```
		- 生成`GitLabBV.gitlab.license` `license_key` `license_key.pub`
		  ```bash
		  ruby license.rb
		  ```
		- 替换默认公钥
		  ```bash
		  cp -f license_key.pub /opt/gitlab/embedded/service/gitlab-rails/.license_encryption_key.pub
		  ```
		- 修改`/opt/gitlab/embedded/service/gitlab-rails/ee/app/models/license.rb`，替换`STARTER_PLAN`为`ULTIMATE_PLAN`
		  ```ruby
		  --- /opt/gitlab/embedded/service/gitlab-rails/ee/app/models/license.rb
		  +++ /opt/gitlab/embedded/service/gitlab-rails/ee/app/models/license.rb
		  @@ -367,7 +367,7 @@
		      end
		      def plan
		      - restricted_attr(:plan).presence || STARTER_PLAN
		      + restricted_attr(:plan).presence || ULTIMATE_PLAN
		      end
		      def edition
		  ```
		- 重新配置gitlab
		  ```bash
		  gitlab-ctl reconfigure
		  gitlab-ctl restart
		  ```
		-
	- #### Docker安装GitLab
		- #Docker
		- 参考：https://juejin.cn/post/6991435962303643679 3.2创建方法二
		- 创建`docker-compose.yml`文件，并在该文件所在的文件夹目录下运行`docker-compose up -d`
		- 需要事先安装`docker-compose`
		- [安装docker-compose](https://link.juejin.cn?target=https%3A%2F%2Fyeasy.gitbook.io%2Fdocker_practice%2Fcompose%2Finstall "https://yeasy.gitbook.io/docker_practice/compose/install")
		- ```docker-compose
		  version: '2'
		  services:
		      gitlab:
		        image: 'gitlab/gitlab-ee:latest'
		        container_name: "gitlab-example"
		        restart: always
		        hostname: '主机ip'
		        environment:
		          TZ: 'Asia/Shanghai'
		          GITLAB_OMNIBUS_CONFIG: |
		            external_url 'http://主机ip:8088'
		            gitlab_rails['gitlab_shell_ssh_port'] = 10080
		            gitlab_rails['time_zone'] = 'Asia/Shanghai'
		        ports:
		          - '18088:8088'
		          - '10080:22'
		          - '443:443'
		        volumes:
		          - /usr/local/gitlab/config:/etc/gitlab
		          - /usr/local/gitlab/logs:/var/log/gitlab
		          - /usr/local/gitlab/data:/var/opt/gitlab
		  ```
		- **注**：端口和映射目录可根据需要修改
		  若开放访问端口为`80`，`external_url`可不加端口号，默认80
		-