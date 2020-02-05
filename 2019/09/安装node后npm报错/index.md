# 安装node后npm报错

# npm install 报错（npm ERR! errno -4048，Error: EPERM: operation not permitted...）
解决方法:
* 方法一：清理下缓存就行，不用管理员权限。
删除npmrc文件。
> 不是nodejs安装目录npm模块下的那个npmrc文件。而是在 C:\Users\{账户}\下的.npmrc文件
* 方法二：直接用命令清理就行，控制台输入：
npm cache clean --force

