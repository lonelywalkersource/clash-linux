## Linux Clash

### 1:进入家目录 并下载代码（调整了部分脚本代码）
```shell
cd ~
git clone https://github.com/Elegycloud/clash-for-linux-backup.git ClashLinux
```
2:修改 .env 文件
```
export CLASH_URL='订阅地址'
export CLASH_SECRET=''
```
3:执行命令
```shell
sudo bash clash-linux-backup/start.sh
```
4:加载环境变量
```shell

```
5:设置环境变量
```shell
cat>~/.bashrc_clash<<EOF
alias proxy_start='sudo bash ~/ClashLinux/start.sh';
alias proxy_down='sudo bash ~/ClashLinux/shutdown.sh';
alias proxy_restart='sudo bash ~/ClashLinux/restart.sh';
# 开启系统代理
proxy_on() {
        export http_proxy=http://127.0.0.1:7890
        export https_proxy=http://127.0.0.1:7890
        export no_proxy=127.0.0.1,localhost
        export HTTP_PROXY=http://127.0.0.1:7890
        export HTTPS_PROXY=http://127.0.0.1:7890
        export NO_PROXY=127.0.0.1,localhost
        echo -e "\033[32m[√] 已开启代理\033[0m"
}

# 关闭系统代理
proxy_off(){
        unset http_proxy
        unset https_proxy
        unset no_proxy
        unset HTTP_PROXY
        unset HTTPS_PROXY
        unset NO_PROXY
        echo -e "\033[31m[×] 已关闭代理\033[0m"
}
EOF
```
6:加载环境变量
```shell
grep -Fxq "source .bashrc_clash" ~/.bashrc || echo 'source .bashrc_clash' >> ~/.bashrc
cd ~ && source .bashrc
```