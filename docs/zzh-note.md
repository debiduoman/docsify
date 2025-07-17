# cursor注册教程

> 本教程主要针对cursor注册用户
> 适用于新用户注册网易163邮箱和cursor账号的步骤。
> 本教程主要参考 https://github.com/yuaotian/go-cursor-help/blob/master/README_CN.md

> [!NOTE]
> 本教程主要针对新用户注册cursor账号，旧用户请参考旧版教程。

## 注册163邮箱账号 
1. 打开[网易163邮箱注册页面](https://mail.163.com/register/index.htm#/normal).  
2. 填写注册信息，包括用户名、密码等。
3. 完成验证码验证。


## 下载cursor
1. 打开[cursor下载页面](https://www.cursor.com/).  
2. 下载cursor安装包。
3. 完成安装。


## 注册cursor账号
1. 打开[cursor下载页面](https://www.cursor.com/).  
2. 填写注册信息，包括用户名、密码等。
3. 完成注册。

## 后续换新号
> [!NOTE] 参考文档
> https://github.com/yuaotian/go-cursor-help/blob/master/README_CN.md
1. 以管理员打开powershell
2. 在管理员终端中输入重置脚本:

```powershell
irm https://aizaozao.com/accelerate.php/https://raw.githubusercontent.com/yuaotian/go-cursor-help/refs/heads/master/scripts/run/cursor_win_id_modifier.ps1 | iex 
```

增强版脚本：
```powershell
irm https://aizaozao.com/accelerate.php/https://raw.githubusercontent.com/yuaotian/go-cursor-help/refs/heads/master/scripts/run/cursor_win_id_modifier_new.ps1 | iex 
```

> [!NOTE]
> 解决方案 1: 快速重置（推荐）
> 关闭Cursor应用
> 运行机器码重置脚本（见下方安装说明）
> 重新打开Cursor继续使用
> 
> 解决方案 2: 切换账号
> 文件 -> Cursor设置 -> 退出登录
> 关闭Cursor
> 运行机器码重置脚本
> 使用新账号登录

## 参考
> [!NOTE]
> 参考文档
> https://github.com/yuaotian/go-cursor-help/blob/master/README_CN.md