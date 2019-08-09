# youku_mini_crawler

某天，一个朋友发了一个优酷的微信小程序给我，问我学计算机的能不能把视频下下来，一开始以为很简单，后来发现优酷小程序是一个独立的视频平台，视频在官网也找不到，而且小程序也没有相关下载的途径，后来查了查资料，因为优酷视频的真实链接是动态变化的，而每个视频的ID是不变的，比如在链接http://v.youku.com/v_show/id_XNjUzNDQwMzIw.html中，“XNjUzNDQwMzIw”就是视频的唯一ID标识，通过这个ID可以通过GET方式请求“http://v.youku.com/player/getPlayList/VideoIDS/”+ID产生的新链接，得到json格式的视频信息，然后组装成视频的真实链接，这个真实链接也是有时效性的，而且向这个真实链接发起请求的时候必须把头的Referer设为www.youku.com骗过服务器才能下载，所以我没有像以前一样用os.system('wget '+url)这样搞起。还有，优酷对大的视频是分段的，所以得到的真实url我存在一个List里面，下载的时候会显示出共有几段以及实时下载了多少段。
