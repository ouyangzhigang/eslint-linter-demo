
### husky
step.1
```shell
npm set-script prepare "husky install" 
```
step.2
```shell
npm run prepare
```

step.3
```shell
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

### commitlint
step.4
```shell
npm i commitlint @commitlint/config-conventional -D
```
step.5
```shell
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

### commitizen
step.6
```shell
npm i commitizen cz-conventional-changelog -D
```
step.7
```shell
npm set-script commit "git-cz" 
```
step.8
```shell
npx commitizen init cz-conventional-changelog --save-dev --save-exact
```

### cz
step.9
```shell
npm i -D commitlint-config-cz  cz-customizable
echo > .cz-config.js
```
step.10

`.cz-config.js`
```javascript
module.exports = {
  types: [
    {
      value: ':sparkles: feat',
      name: '✨ feat:     新功能'
    },
    {
      value: ':bug: fix',
      name: '🐛 fix:      修复bug'
    },
    {
      value: ':package: build',
      name: '📦️ build:    打包'
    },
    {
      value: ':zap: perf',
      name: '⚡️ perf:     性能优化'
    },
    {
      value: ':tada: release',
      name: '🎉 release:  发布正式版'
    },
    {
      value: ':lipstick: style',
      name: '💄 style:    代码的样式美化'
    },
    {
      value: ':recycle: refactor',
      name: '♻️  refactor: 重构'
    },
    {
      value: ':pencil2: docs',
      name: '✏️  docs:     文档变更'
    },
    {
      value: ':white_check_mark: test',
      name: '✅ test:     测试'
    },
    {
      value: ':rewind: revert',
      name: '⏪️ revert:   回退'
    },
    {
      value: ':rocket: chore',
      name: '🚀 chore:    构建/工程依赖/工具'
    },
    {
      value: ':construction_worker: ci',
      name: '👷 ci:       CI related changes'
    }
  ],
  messages: {
    type: '请选择提交类型(必填)',
    customScope: '请输入文件修改范围(可选)',
    subject: '请简要描述提交(必填)',
    body: '请输入详细描述(可选)',
    breaking: '列出任何BREAKING CHANGES(可选)',
    footer: '请输入要关闭的issue(可选)',
    confirmCommit: '确定提交此说明吗？'
  },
  allowCustomScopes: true,
  // 跳过问题
  skipQuestions: ['body', 'footer'],
  subjectLimit: 72
}
```
step.11
```shell
npm set-script commit "git add . && cz-customizable"
```
### emoji
step.12
```shell
npm i -D  commitlint-config-git-commit-emoji 
```

step.13

update `commitlint.config.js`
```javascript
module.exports = {
  extends: ['git-commit-emoji', 'cz']
}
```