# Resolution Studio

用于图像空间分辨率分析的桌面工具，提供 **刃边 MTF** 与 **线对卡 CTF** 两种测量模式。支持独立运行，也可作为 ImageJ / Fiji 插件使用。

**[下载最新版本](https://github.com/Nanamiwww/resolution-studio/releases/latest)** · **[完整使用说明](使用说明.txt)** · **[问题反馈](https://github.com/Nanamiwww/resolution-studio/issues)**

## 下载与启动

在 [Releases](https://github.com/Nanamiwww/resolution-studio/releases) 的 **Assets** 中下载 `Resolution-Studio-1.5.2.zip`，完整解压后使用。

| 使用方式 | 操作 | 运行要求 |
| --- | --- | --- |
| Windows 独立版 | 双击 `启动 Resolution Studio.bat` | Java 8 或更新版本 |
| ImageJ / Fiji 插件 | 将 `插件版/Resolution_Studio.jar` 复制到 ImageJ / Fiji 的 `plugins` 文件夹，重启后选择 **Plugins → Resolution Studio** | 已安装 ImageJ 或 Fiji |

独立版已包含 ImageJ 1.54u 内核与界面库，不需要另装 ImageJ；**下载不包含 Java 运行**。Windows 启动器会查找已安装或 ImageJ / Fiji 自带的 Java，找不到时会给出中文提示。

下载包没有预设机器专属的 `java-path.cfg`，首次启动后由启动器生成。完整包内还附有三张模拟示例图像、使用说明、源码包与第三方许可文件。

## 主要功能

- **刃边 MTF**：矩形选区分析，显示 MTF、ESF、LSF、MTF20 / MTF10、刃边倾角及质量提示。
- **线对卡分析**：灰度剖面、峰谷分组、对比度与 CTF；支持手动分组、标称频率、参照组和分辨率判定。
- **标定与图像处理**：手动或按已知长度标定像素尺寸，显示标定来源；支持多帧图像及颜色 / 灰度处理选择。
- **导入与导出**：支持 TIFF、DICOM、PNG 等图像和 RAW 导入；导出 CSV 数据、PNG 图表及结果摘要。
- **项目与对比**：保存 `.rsproj` 项目，叠加历史曲线，并保留测量参数、来源和警告信息。

## 1.5.2 更新重点

以下内容根据随包更新记录整理：

- 保存、关闭、导出等操作会先应用输入框中尚未按回车的数值。
- 无效或越界输入会提示并保留，避免错误数值被截断后使用。
- 修改线宽、切换图像状态时保留线对的手动分组、标称值和参照组；暂时无法对应的修改继续保留。
- 改善全角数字处理、主题切换及使用说明窗口滚动。

详细变更与历史版本记录见[使用说明](使用说明.txt)。

## 测量说明

分析前请确认像素尺寸、测量方向和图像数值来源。线对卡结果可能以插值、估计、区间或下限形式给出，应结合程序显示的条件解释。CTF 及其换算结果与直接测得的刃边 MTF 需区分。

刃边模式默认不旋转图像；旋转计算为实验性选项。随包示例是模拟图像，用于熟悉操作。

## 源码与构建

完整包中的 `源码.zip` 包含程序源码、测试和构建脚本；也可从 Release 单独下载 `Resolution-Studio-1.5.2-source.zip`。

源码包的 `build.sh` 需要 **Bash、Git 和 JDK 11 或更新版本**，会联网取得指定提交的 ImageJ 与 FlatLaf 源码，并在生成 JAR 前运行回归测试。在具备这些工具的环境中，进入源码目录后运行：

```bash
bash build.sh
```

源码中的 `make_release.sh` 依赖开发工作区的目录布局，首次构建请使用 `build.sh`。本次发布沿用所提供的 1.5.2 JAR 文件。

## 第三方组件与校验

使用 ImageJ 和 FlatLaf；第三方许可文件保留在完整包的 `licenses/` 文件夹中，并在仓库提供副本。

发行页面提供 `SHA256SUMS.txt`，用于核对完整包和源码包的完整性。GitHub 自动生成的 `Source code` 归档是仓库内容快照，使用软件请下载上面指定的完整包。
