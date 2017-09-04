# golb
获取当前时间的毫秒数：

    const timeNow = new Date().getTime()
获取特定时间的毫秒数：
假设获得的时间格式为  '2017-10-01 18:15:19'

    const getTime = '2017-10-01 18:15:19'
所以，这个特定时间的毫秒数应该为：

    const timeOver = Date.parse(new Date(getTime.replace(/-/g, '/')))
其中，时间中的短横杠应该被替换为 '/',以获得safari浏览器的支持。
