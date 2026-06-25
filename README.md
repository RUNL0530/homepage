# 我的个人主页

这是一个可以部署到 GitHub Pages 的静态个人主页。页面本身由 `index.html` 提供，数据同步继续使用 Firebase Google 登录和 Firestore。

## 部署到 GitHub Pages

1. 在 GitHub 创建一个新仓库，例如 `homepage-project`。
2. 把本目录内容推送到仓库的 `main` 或 `master` 分支。
3. 进入仓库的 `Settings` -> `Pages`。
4. 在 `Build and deployment` 里选择 `Deploy from a branch`。
5. 选择你的分支和根目录 `/`，保存后等待 GitHub 部署。
6. 部署完成后访问：

```text
https://你的用户名.github.io/仓库名/
```

如果仓库名是 `你的用户名.github.io`，访问地址通常是：

```text
https://你的用户名.github.io/
```

## Firebase 登录配置

这个页面已经保留现有 Firebase 配置。上传到 GitHub Pages 后，如果 Google 登录失败，需要到 Firebase 控制台添加授权域名：

1. 打开 Firebase Console。
2. 进入当前项目 `runl-85bf0`。
3. 打开 `Authentication` -> `Settings` -> `Authorized domains`。
4. 添加你的 GitHub Pages 域名：

```text
你的用户名.github.io
```

如果你本地直接打开 `index.html` 测试，Firebase 登录可能会受浏览器和授权域名限制；GitHub Pages 的 HTTPS 地址配置好授权域名后更稳定。

## 数据保存

- 未登录时：数据保存在当前浏览器的 `localStorage`。
- 登录后：数据保存在 Firestore 的 `users/{uid}` 文档。
- 页面刷新不会自动增加“今日已学”单词数，只有点击“换一个”并抽到未学过的单词时才计数。
