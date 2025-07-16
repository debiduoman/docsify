# 记录一次解决 git push 网络问题的经历

大家好，今天我将分享一次在将我的 Docsify 博客部署到 GitHub Pages 时，遇到的 `git push` 网络连接问题的排查和解决过程。这个过程虽然有点波折，但也让我学到了处理 Git 网络问题的新技巧，特别是了解了一些之前没用过的 `git` 命令。

### 酷炫的初体验：预想中的浏览器授权

项目初始化、添加文件、本地提交……一切都顺风顺水。到了最关键的一步：将本地仓库推送到 GitHub 远程仓库。

我满怀期待地敲下 `git push -u origin main` 命令。

根据以往的经验，**在推送一个新项目时，一个很酷的体验是 Git 会自动打开浏览器，弹出一个授权页面，要求我登录并授权 GitHub 凭据**。这让整个身份验证过程无缝又现代。

然而，这一次，我没有等到预想中的浏览器窗口，等来的却是……

### 遭遇挫折：恼人的网络错误

终端无情地打出了第一条错误信息：

```
fatal: unable to access 'https://github.com/debiduoman/docsify.git/': Recv failure: Connection was reset
```

"连接被重置"，这通常意味着网络不稳定。于是我重试了几次，但问题依旧。在尝试调整了 Git 的 `http.postBuffer` 配置后，错误信息变得更加直白：

```
fatal: unable to access 'https://github.com/debiduoman/docsify.git/': Failed to connect to github.com port 443...
```

很明显，我的本地网络环境和 GitHub 服务器之间的 HTTPS (443端口) 连接存在着持续性的障碍。

### 柳暗花明：切换协议与 set-url 的惊艳亮相

既然 HTTPS 的路走不通，是时候换一条路了——使用更稳定、不易受网络环境干扰的 SSH 协议。

在确认了本地已经存在 SSH 密钥后，我学到了这次经历中最关键的一步，也是一个非常酷的知识点：**如何将一个已存在的远程仓库地址从 HTTPS 修改为 SSH**。

我之前可能以为需要先 `remote remove` 再 `remote add`，但其实一条命令就可以搞定：

```bash
git remote set-url origin git@github.com:debiduoman/docsify.git
```

**`git remote set-url` 这个命令实在是太优雅了！** 它直接更新了 `origin` 这个远程地址的 URL，操作清晰明了，让我印象深刻。

在将 GitHub 账户与我的电脑公钥关联后，我再次执行了 `git push`。

这一次，终端终于传来了好消息，代码被顺利推送到了远端。

### 总结

这次经历提醒我们，当遇到棘手的网络问题时，不要只在一个方向上死磕。切换协议（如 HTTPS -> SSH）往往是釜底抽薪的有效方法。而 `git remote set-url` 这个命令，也成为了我工具箱里一个值得收藏的利器。

希望我的这段经历能对遇到类似问题的朋友有所帮助！ 