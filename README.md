# 与游戏中心的少女异文化交流的故事 字幕仓库

该仓库存放以`北宇治字幕组`名义制作的TV动画《与游戏中心的少女异文化交流的故事》 字幕。

![Poster for Gacen-girl](https://github.com/user-attachments/assets/a750465e-ee0d-4c69-b076-67ed1a8490da)

## 下载字幕

[![status badge main branch](https://github.com/Kitauji-Sub/subs-gacen-girl/actions/workflows/build-subtitle.yml/badge.svg?branch=main)](https://github.com/Kitauji-Sub/subs-gacen-girl/releases/latest) ![GitHub Release](https://img.shields.io/github/v/release/Kitauji-Sub/subs-gacen-girl)


可前往 Releases 下载最新字幕文件：[Release](https://github.com/Kitauji-Sub/subs-gacen-girl/releases/latest)

<!-- 可在此处下载所使用的字体：[字体](https://github.com/Kitauji-Sub/subs-gacen-girl/releases/tag/typeface) -->

## 开发

### 环境需求

+ Aegisub
  + [DependencyControl (optional)](https://github.com/TypesettingTools/DependencyControl)
  + [Merge Scripts](https://github.com/TypesettingTools/Myaamori-Aegisub-Scripts)
  + [The0x539's templater](https://github.com/The0x539/Aegisub-Scripts/blob/trunk/src/0x.KaraTemplater.moon)
+ Python 3.x
  + SubDigest

> [!CAUTION]
> Merge Scripts 当前版本存在一个 bug ，会使导出的字幕文件中存在重复样式，所以下文构建步骤使用了 FichteForks 的 pr。
>
> 参见https://github.com/TypesettingTools/Myaamori-Aegisub-Scripts/issues/26

### 目录结构

对于每个单集的目录结构如下图所示：

```
epxx → 主目录
├── screen
│   └── screen.ass
└── epxx.ass
```

`epxx.ass`为主文件，包含`import`语句。子文件应使用 `Merge Scripts` 经由`import`语句导入到主文件中，最后导出发布文件。

### 修改字幕

应对每个单集下的各个文件进行修改。在增删主文件对话行时，应注意保持特效栏文本为`kara`。

修改完成后，进行字幕文件的构建。

#### Github Actions 构建

1. [Fork](https://github.com/Kitauji-Sub/subs-gacen-girl/fork)本仓库
2. Commit 后提交到仓库
3. 在 Actions 选项卡下查看 workflow run，在 Artifacts 中下载 gcg_subs_built

> [!NOTE]
> 如果在commit message中加入[PATCH]则会使版本号第三位增加，并把构建出的字幕文件发布到release。

#### 本地构建

1. 克隆本仓库到本地
2. 下载[Aegisub CLI](https://github.com/scrpr/aegisub-cli/releases/download/disable_unique_path/aegisub-cli.zip)，解压到仓库根目录/aegisub-cli/下
3. 下载[字体](https://github.com/Kitauji-Sub/subs-gacen-girl/releases/download/typeface/fonts.zip)，安装或使用FontLoader类工具临时加载
4. 安装依赖库
```
pip install --user git+https://github.com/FichteForks/Myaamori-Aegisub-Scripts.git@pr/fix-style-deduplication#subdirectory=scripts/sub-digest
pip install requests urllib3
```
5. 运行Python脚本
```
python build_scripts/build.py <path>/<to>/<work_dir>
```
6. 在`builds/output`下查看输出的字幕文件

## 声明

![site image](https://zhconvert.org/build/assets/images/logo_h36.1306fa53.png)

本仓库字幕在繁体中文化流程中，使用了繁化姬（[zhconvert.org](https://zhconvert.org/)）提供的 API 服务。

繁化姬API仅供个人学习研究使用，商业用途请参考[繁化姬说明文件](https://docs.zhconvert.org/commercial/)