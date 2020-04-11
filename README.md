云 menuconfig（SSH 连接到 Actions）

通过 tmate 连接到 GitHub Ac­tions 虚拟服务器环境，可直接进行 make menuconfig 操作生成编译配置，或者任意的客制化操作。也就是说，你不需要再自己搭建编译环境了。这可能改变之前所有使用 GitHub Ac­tions 的编译 Open­Wrt 方式。

编辑 workflow 文件（.github/workflows/build-openwrt.yml），修改SSH_ACTIONS环境变量的值为true。（或者也可以不修改，而是通过 webhook 方式发送带有ssh触发关键词的请求。）

SSH_ACTIONS: true

在触发工作流程后，在 Actions 页面等待执行到SSH connection to Actions步骤，会出现下面的信息。

To connect to this session copy-n-paste the following into a terminal or browser:

ssh Y26QeagDtsPXp2mT6me5cnMRd@nyc1.tmate.io

https://tmate.io/t/Y26QeagDtsPXp2mT6me5cnMRd

复制 SSH 连接命令粘贴到终端内执行，或者复制链接在浏览器中打开使用网页终端。（网页终端可能会遇到黑屏的情况，按 Ctrl + C 即可）

cd openwrt && make menuconfig

完成后按快捷键Ctrl+D或执行exit命令退出，后续编译工作将自动进行。

TIPS: 固件目录下有个config.seed文件，如果你需要再次编译可以使用它。
WARRING: 默认连接30分钟后会断开并终止编译工作流程，防止资源浪费与封号风险。如果你想解除这个限制，可以根据提示操作，但导致的一切后果请自行承担。
