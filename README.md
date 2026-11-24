# 最后一次排名

校园悬疑视觉小说，鱼尾视角，推理与感情互动约按 7:3 设计。学校、人物及案件均按虚构设定创作。包含死亡、少量血迹与心理压力描写；恋爱克制，无露骨内容。

## 立即游玩

解压后用 Chrome、Edge、Firefox 或 Safari 打开 **index.html**。所有资源随包提供，断网也可运行。不需要安装 Node、运行构建、配置数据库或连接 API。建议首次阅读预留约 40 分钟；实际时长取决于阅读速度与推理停留时间，并非真人计时结果。

本版是完整可通关的精简首版：8 章、259 段主体对白及旁白、18 条线索、8 轮证据对质、7 块章末推理板、7 个结局。图像为原创程序绘制的简化平面风格，包含 9 张背景、25 张透明人物表情和 7 张结局插图；不含配音。两首短环境音乐会循环播放，可在设置中静音。

## 操作

- 点击对话框推进；文字未显示完时，第一次点击补全，第二次点击前进。
- 对话框取得焦点时，空格或回车推进。按钮取得焦点时，空格或回车按浏览器标准激活该按钮。
- Ctrl 或长按对话框：仅快进已读内容。首次遇到的对白不会跳过。自动播放遇到调查、选项或推理时停止。
- H：回看；S：存档；Esc：菜单或关闭窗口。切换到后台、失焦或打开菜单会停止自动播放。
- 点击场景标记阅读线索，再点击“收录并返回场景”。本场景线索收齐后点击“线索已齐 · 继续”。
- 对质从已有线索选择反证；推理板选择每条证据支持的判断。错误扣 1 点冷静值，耗尽后可恢复重试或从本章重来。
- 只有明确选择公开错误指控、隐去关键证据等关键分支，才走向失败或普通结局。普通推理失误不直接结束故事。
- 人物关系只显示阶段，不显示数字。终章邀请不覆盖此前选择；个人结局要求关键推理完整，关系达到门槛且为最高者。并列时按终章选择决定。

## 存档与回放

3 个手动槽、1 个自动槽。槽位显示章节、保存时间和对白摘要。自动槽在剧情节点变化时更新，不要把它当成多版本备份。存档包含当前章节位置、线索、关系、推理完成情况、冷静值、分支及待续对白；设置、已读标记与图鉴另存为浏览器资料。

浏览器拒绝 localStorage 时使用内存降级并提示，此时关闭页面会失去内存进度。通过“存档与迁移”导出 JSON 文本，复制保存到自己的文本文件；在另一浏览器或部署后的页面粘贴并导入。导入校验游戏名、版本、章节位置、线索及人物等字段，不执行存档中的代码。进度导出不包含其他手动槽或整个图鉴。

章节回放仅开放已经到达的章节，使用首次到达时的状态快照，不凭空补发线索或好感。回放会替换当前未保存进度，界面会提示。新游戏保留图鉴与已读标记。建议同一时间只用一个标签页游玩，避免不同窗口争用自动槽。

## 部署到 GitHub Pages

1. 在 GitHub 新建仓库，例如 last-ranking；公开仓库可使用免费 Pages。
2. 上传本目录中的全部内容。**index.html 必须位于仓库根目录**，不要把解压后的外层 last-ranking 文件夹作为唯一目录上传。保留空文件 .nojekyll。
3. 如果使用 Git，在本目录终端执行以下命令。替换 USERNAME 为自己的用户名；GitHub 认证按本机配置完成。

~~~sh
git init
git add .
git commit -m "Add playable visual novel"
git branch -M main
git remote add origin https://github.com/USERNAME/last-ranking.git
git push -u origin main
~~~

4. 仓库 Settings → Pages → Build and deployment，Source 选 Deploy from a branch，Branch 选 main，目录选 / (root)，保存。
5. 等待 Pages 部署完成，访问 https://USERNAME.github.io/last-ranking/ 。更改仓库名时，相应调整网址。
6. 本站使用相对资源路径，不依赖网站根路径，可运行在上述仓库子路径内。

本次交付没有替你创建远程仓库或发布站点。

## 本地服务器验证

直接打开 HTML 即可玩。需要模拟 Pages 子路径时，可在本项目的父目录执行：

~~~sh
python3 -m http.server 8000
~~~

Windows 若命令名为 python，使用 python -m http.server 8000。然后访问 http://localhost:8000/last-ranking/ 。浏览器地址栏应包含项目目录名，避免只测服务器根路径。

## 文件结构

~~~text
index.html                 入口
.nojekyll                  Pages 静态部署标记
css/style.css              布局、颜色变量、响应式与减少动效
js/engine.js               数据驱动剧情状态机与输入
js/ui.js                   界面、资源回退、图鉴、预加载
js/deduction.js            调查、证据对质、推理板
js/save.js                 浏览器存档、校验与文本迁移
js/audio.js                本地音乐与 Web Audio 提示音
data/config.js             体验与结局门槛参数
data/characters.js         人物公开介绍
data/assets-config.js      全部资源映射
data/clues.js              证据及来源
data/endings.js            结局正文和唯一判定函数
data/story.js              章节、场景及剧情指令
assets/bg/                 9 张 1920×1080 WebP 背景
assets/characters/         25 张 680×1700 透明 PNG
assets/cg/                 7 张 1440×810 结局插图
assets/audio/              原创 calm.wav、tension.wav
assets/source/             可编辑 SVG 原始绘图
STORY.md                   完整故事大纲与结局说明，含剧透
SELF_CHECK.md              实际自检结果与测试范围
MANIFEST.txt               每个文件的清单
~~~

## 替换图片和音乐

所有路径在 data/assets-config.js 中配置，必须以 ./ 开头或使用等价相对路径。文件名区分大小写；推荐小写英文，无空格。不要引入外部 CDN、字体、图片 URL。

角色目录为 youzi、huge、mage、yuanba。基本表情 normal.png、smile.png、sad.png、angry.png、surprised.png、nervous.png；马哥另有 hollow.png。建议透明 PNG/WebP，高 1600–2000 像素。所有表情应保持相同画布、人物大小和落脚位置，否则切换会跳动。本版为 680×1700 PNG。

背景建议 1920×1080 的 WebP/JPG；更换格式时同步修改映射。编号对应 classroom、corridor、stairs、office、gym、gate、club、canteen、roof。结局 CG 在 cg 对象中按结局 ID 配置。背景不存在时显示程序生成的色块标签，角色不存在时显示名字与剪影；每个失败路径只警告一次，不阻塞剧情。

音乐在 audio 对象中配置。本版 WAV 是短循环氛围音，音乐缺失会静默跳过。首次用户操作后才启用声音，音量与静音保存在设置中。提示音由浏览器合成。

首屏只加载必要背景，开始故事时显示当前章预加载进度，进入章节后后台预载下一章。建议整个站点保持在 50MB 以内。assets/source 是可选的编辑原稿，删去不会影响游戏。

## 修改剧情

story.js 内部使用少量辅助函数构建纯数据，最终导出 window.STORY。结构为章节 → 场景 → commands。引擎、界面和剧本分离；脚本用普通 script 标签按顺序载入，不使用 ES Modules，也不 fetch JSON。

以下是一段可替换章节的完整结构示例；示例复用已经存在的素材、人物、线索和结局判定，不要直接把它覆盖到正式剧本后仍期待全部七结局可达。

~~~js
window.STORY = [{
  id: 'example', title: '示例章', summary: '一条待核对的消息',
  scenes: [{
    name: '放学后 / 教室', bg: 'classroom',
    commands: [
      { type: 'background', id: 'classroom' },
      { type: 'audio', id: 'calm' },
      { type: 'show', who: 'youzi', expression: 'normal', position: 'left' },
      { type: 'narrate', text: '我把两份成绩记录摊在桌上。' },
      { type: 'say', who: '柚子', text: '先核对来源，再讨论原因。' },
      { type: 'clue', id: 'paper' },
      { type: 'choice', text: '如何回应？', options: [
        { text: '一起核对', affection: { youzi: 2 }, flag: { agreed: true }, reply: '我把笔递给他。' },
        { text: '先自己整理', reply: '我想先把问题写完整。' }
      ] },
      { type: 'if', flag: 'agreed', jumpLabel: 'together' },
      { type: 'narrate', text: '我独自圈出了待核对的数字。' },
      { type: 'jump', label: 'review' },
      { type: 'label', id: 'together' },
      { type: 'affection', who: 'youzi', value: 1 },
      { type: 'say', who: '柚子', text: '谢谢你愿意听我解释。' },
      { type: 'label', id: 'review' },
      { type: 'investigate', id: 'desk', title: '检查桌面', items: [
        { clue: 'rank', rect: [10, 20, 25, 22] }
      ] },
      { type: 'confront', id: 'proof', text: '分布异常就足以证明改分吗？',
        answer: 'paper', success: '原始记录支持差异，但操作人还需核查。', hint: '寻找原始依据。' },
      { type: 'board', id: 'b1', title: '核对证据', rows: [
        { clue: 'paper', question: '签收单说明什么？', options: ['存在成绩差异', '已经证明凶手'], answer: 0 }
      ] },
      { type: 'hide' },
      { type: 'ending' }
    ]
  }]
}];
~~~

position 支持 left、center、right；同一站位只显示一人。调查 rect 使用可调查区域中的百分比 x、y、宽、高，按钮仍保留最小触控高度。choice 的 jump 是目标章节 ID；if 的 jumpLabel 和 jump 指令的 label 都是当前章节内标签。

对话显示名使用 who 字符串；角色出场使用英文人物 ID。线索必须先在 clues.js 注册。章末推理的答案下标从 0 开始，正式剧本末尾会打散选项位置并同步答案。

全部结局判定集中在 endings.js：错误指控优先 → 隐瞒或关键推理不完整 → 玩家选择独行 → 最高且达标的关系 → 真相结局。新增章节或修改关键推理时，连同 b1–b6 判定列表、存档校验允许列表及版本号一起更新。大幅修改指令顺序会使旧位置存档失去意义，应增加 config.js 的 version 并更换 storageKey；不要声称任意新版都兼容旧存档。

字体为系统字体栈，主色在 CSS :root 变量中。减少动效跟随 prefers-reduced-motion。更多事实核对、分支与边界见 SELF_CHECK.md。
