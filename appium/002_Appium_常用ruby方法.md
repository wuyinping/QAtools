```ruby
# 创建driver，启动app
require 'appium_lib'

cap = {platformName: :android,deviceName: :android,app: './api.apk'}
driver = Appium::Driver.new(caps: cap)
dirver.start_driver

# 重启driver
driver.restart

# 退出driver
driver.driver_quit

# 设置等待时间
driver.set_wait

# 判断一个element是否存在
driver.exists

# 截屏
driver.screenshot('D:\rubytest\test.png')

```