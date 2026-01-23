# openwrt-ci

bulid openwrt

# 修改内容

为rax3000m、ax3000t编译小固件，只保留clash、应用过滤、lucky，tailscale使用另外一种小固件部署方式（shell部署），

## 修复配置文件（config文件）说明

自定义固件配置，将config文件的内容复制到仓库里的config文件里

生成config文件详细教程请到[lede的仓库查看](https://github.com/coolsnowwolf/lede)

<details>
<summary><b>&nbsp;查看如何生成config文件</b></summary>

1. 首先装好 Linux 系统，推荐 Debian 11 或 Ubuntu LTS

2. 安装编译依赖环境

   ```bash
   sudo apt update -y
   sudo apt full-upgrade -y
   sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
   bzip2 ccache cmake cpio curl device-tree-compiler fastjar flex gawk gettext gcc-multilib g++-multilib \
   git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libglib2.0-dev libgmp3-dev libltdl-dev \
   libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libreadline-dev libssl-dev libtool lrzsz \
   mkisofs msmtp nano ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 python3-pyelftools \
   libpython3-dev qemu-utils rsync scons squashfs-tools subversion swig texinfo uglifyjs upx-ucl unzip \
   vim wget xmlto xxd zlib1g-dev
   ```

3. 下载源代码，更新 feeds 并安装到本地

   ```bash
   git clone --depth=1 https://github.com/hanwckf/immortalwrt-mt798x.git
   cd lede
   ./scripts/feeds update -a
   ./scripts/feeds install -a
   ```

4. 命令行输入 `make menuconfig` 选择配置，选好配置后保存，文件名自定义为xxx.config（xxx是自定义的）

   ```bash
   make defconfig
   ./scripts/diffconfig.sh > seed.config
   ```

5. 命令行输入 `cat xxx.config` 查看这个文件，也可以用文本编辑器打开

6. 复制 xxx.config 文件内所有内容到 configs 目录对应文件中覆盖就可以了

   **如果看不懂编译界面可以参考 YouTube 视频：[软路由固件 OpenWrt 编译界面设置](https://www.youtube.com/watch?v=jEE_J6-4E3Y&list=WL&index=7)**
   </details>
