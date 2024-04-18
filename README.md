## Figma URL

[Unsplash Images](https://www.figma.com/file/O2MaAAlr4nznh7m53azatL/Unsplash-images?node-id=0%3A1&t=cYDOCgqOs9IX2If0-1)

### 操作指南

- #### 设置

  - 运行 `npm install` 安装项目依赖
  - 运行 `npm run dev` 启动本地开发环境

#### 初始结构与全局上下文

创建三个组件：ThemeToggle、SearchForm 和 Gallery，并在 App.jsx 中渲染这三个组件。设置全局上下文。

#### 深色主题 - 初始配置

在全局上下文中创建名为 `isDarkTheme`（布尔值）的状态变量和一个辅助函数 `toggleDarkTheme`，当调用 `toggleDarkTheme` 函数时将 `isDarkTheme` 的值设为相反状态。将 `isDarkTheme` 和 `toggleDarkTheme` 传递给 ThemeToggle 组件。在 ThemeToggle 组件中，从 React Icons 库导入月亮和太阳图标，并创建一个按钮。当按钮被点击时，调用 `toggleDarkTheme`，并在按钮内根据 `isDarkTheme` 的值显示相应的图标。

#### 添加/移除深色主题样式类

在 `toggleDarkTheme` 函数中添加逻辑，根据 `isDarkTheme` 值向 body 元素添加或移除 `.dark-theme` 类。

#### 深色主题的 CSS

为暗黑模式和正常模式分别创建背景颜色和文本颜色的 CSS 变量，以及用于深色模式过渡效果的 CSS 变量。

```css
:root {
  /* dark mode setup */
  --dark-mode-bg-color: #333;
  --dark-mode-text-color: #f0f0f0;
  --backgroundColor: var(--grey-50);
  --textColor: var(--grey-900);

  --darkModeTransition: color 0.3s ease-in-out, background-color 0.3s
      ease-in-out;
}

.dark-theme {
  --textColor: var(--dark-mode-text-color);
  --backgroundColor: var(--dark-mode-bg-color);
}

body {
  transition: var(--darkModeTransition);
  background: var(--backgroundColor);
  color: var(--textColor);
}
```

#### 针对用户偏好使用暗黑模式的情况：

```css
@media (prefers-color-scheme: dark) {
  :root {
    --textColor: var(--dark-mode-text-color);
    --backgroundColor: var(--dark-mode-bg-color);
  }
}
```

#### 搜索表单结构

创建一个包含输入框和提交按钮的表单。输入框应具有以下属性：type='text'，name='search'，placeholder='cat'，className='form-input search-input'。当用户提交表单时，获取（暂时仅记录）输入框中的值。

#### Unsplash 图片网站介绍

Unsplash 是一个提供大量高质量免费图片素材的网站。Unsplash API 是一项服务，允许开发者在其应用中访问并使用 Unsplash 的图片集及相关数据。API 支持搜索、下载及以多种方式使用图片，例如构建图片画廊或将其整合到社交媒体应用中。许多开发者利用 Unsplash API 来提升其应用或网站的视觉内容质量。

[Unsplash 网站](https://unsplash.com/)

#### 注册 Unsplash 账户并获取 API 密钥

#### [Unsplash API](https://unsplash.com/developers)

要使用 Unsplash API 在你的应用中抓取图片，首先需要在 Unsplash 注册账户以便获取 API 密钥，该密钥可用于验证你的请求。[Unsplash API 开发者中心](https://unsplash.com/developers)

#### 查找 API 密钥和搜索图片的正确 URL

- 注册应用
- 授权（提示：使用公共认证）
- 搜索功能（提示：搜索照片）

注册 Unsplash 账户后，需在 Unsplash 提供的 API 文档中找到你的 API 密钥及其搜索图片所使用的正确 URL。

#### 使用 Thunder Client VS Code 扩展测试 URL

在将 API 集成到应用程序之前，最好先使用 Thunder Client 这样的 VS Code 扩展来测试 URL，确保 URL 正确无误且能成功获取图片。

#### 在 Gallery 组件中安装和设置 React Query

要在应用中从 Unsplash API 获取图片，你需要在 Gallery 组件中安装并设置 React Query。

#### 安装和设置 React Query Dev Tools

React Query Dev Tools 提供了一种检查和调试 React Query 数据缓存行为的方法。要使用此工具，需要在应用中安装并设置 React Query Dev Tools。

#### 在 context.jsx 文件中创建 searchValue 状态值

为了实现搜索功能，你需要在 context 文件（如 context.jsx）中创建一个状态值来存储用户的搜索输入。

#### 修复 useQuery

设置好 React Query 并创建了 searchValue 状态值之后，需要修改 useQuery 函数，使其基于用户的搜索输入获取图片。

#### 使用 JavaScript 检查用户是否偏好暗黑模式

为了提供更好的用户体验，可以通过 JavaScript 访问用户的系统偏好设置，并据此设置应用的主题。

#### 将 isDarkTheme 状态值存储在 localStorage 中

为了跨会话持久化用户首选主题，可以在 localStorage 中存储 isDarkTheme 状态值，使得即使用户关闭并重新打开应用，主题也能保持不变。

#### 在 VITE 中设置环境变量

可以使用环境变量来存储敏感信息，如 Unsplash API 密钥。为了在应用中使用环境变量，需要在 VITE 构建工具中进行设置。

#### 将应用部署至 Netlify 并设置环境变量

完成应用开发后，可将其部署到 Netlify 等托管平台。在部署到 Netlify 时，需要设置环境变量，确保应用能够访问 Unsplash API 密钥。

#### 添加 CSS 样式

最后，可以为应用添加 CSS 样式，使组件外观更精致，提供良好的用户界面。

#### 深色主题类切换代码解释

```js
const body = document.querySelector('body');
body.classList.toggle('dark-theme', newDarkTheme);

// alternative setup
document.body.classList.toggle('dark-theme', newDarkTheme);
```

const body = document.querySelector('body'); - 这行代码使用 document.querySelector() 方法选择当前文档的 body 元素，该方法返回与指定选择器匹配的第一个元素。在这种情况下，它选择了 body 元素。

body.classList.toggle('dark-theme', isDarkTheme); - 这行代码切换了 body 元素的 dark-theme 类。classList 属性是一个只读列表，包含元素的类。toggle() 方法根据情况向元素添加类或移除类。在这种情况下，如果 isDarkTheme 为 true，则添加 dark-theme 类；如果为 false，则移除 dark-theme 类。

#### elements 属性

事件处理函数 handleSubmit 中的 event.target 对象的 elements 属性指的是包含在 <form> 元素内的所有表单控件（例如 input、select、textarea、button 等）的 HTMLCollection。

这非常有用，因为你可以使用 elements 集合在表单提交时获取表单控件的值。例如，e.target.elements.search.value 将在表单提交时给出搜索输入字段的值。

#### React Query 信息

默认情况下，useQuery 缓存 API 请求的结果一段时间。这可以通过减少向 API 发送的请求次数来提高应用程序的性能。

当你在 useQuery 的 options 对象中指定 queryKey 数组时，你告诉该 hook 如何标识正在获取的数据。如果组件重新渲染时 queryKey 数组不变，则 useQuery 将返回缓存的数据，而不是重新从 API 获取。

queryKey 数组由 useQuery 用于标识查询正在获取的数据。当 queryKey 数组发生变化时，useQuery 假定正在获取的数据已经改变，并重新运行 queryFn 来获取更新的数据。

在这种情况下，searchTerm 是用户的搜索输入，它用于修改 API 请求的 URL。通过在 queryKey 数组中包含 searchTerm，你告诉 useQuery 在用户搜索输入发生变化时重新运行 queryFn，以便根据新的搜索词获取更新的数据。

因此，如果不在 queryKey 数组中包含 searchTerm，那么当用户执行新的搜索时，useQuery 将不会重新获取数据。

#### Vite 环境变量

- .env：必须包含在 .gitignore 中
