# k6_win64
 modern load testing tool, using Go and JavaScript - https://k6.io

在windows 平台下，使用步骤：
参考官网，执行以下命令后，
go get -u github.com/loadimpact/k6

The only catch is, if you want the web UI available, it has to be built separately. Requires a working NodeJS installation.


First, install the ember-cli and bower tools if you don't have them already:


npm install -g ember-cli bower

Then build the UI:


cd $GOPATH/src/github.com/loadimpact/k6/web

npm install && bower install

ember build

最重要的地方：

下载 win64压缩包，解压 cmd 命令 执行 k6命令，个人k6解压到 C:\k6_win64 ，需要执行的test.js文件也在这个文件夹中。

在cmd 输入：C:\k6_win64>k6 run  test.js，

执行过程中，可以访问   web ui: http://127.0.0.1:6565/。

test.js内容如下：


import {check} from "k6"

import http from "k6/http";

export let options = {
  vus: 10,
  duration: "30s"
};


export default function() {
  http.get("http://test.loadimpact.com");
};

