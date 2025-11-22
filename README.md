# PaddleOCR C++ Windows CPU 构建项目

## 项目描述

这是一个自动化构建 PaddleOCR C++ 版本的 GitHub Actions 项目，针对 Windows CPU 环境（支持 Windows 7 及以上版本）。项目从 PaddleOCR 官方仓库克隆源码，使用 Visual Studio 2022 和 CMake 编译生成静态链接的 OCR 可执行文件（ppocr.exe）和库文件。

主要特性 ：
* 从源码编译 OpenCV 4.7.0：启用 freetype 和 harfbuzz 支持（用于文本渲染），优先静态库（减少 DLL 依赖）。
* Paddle Inference v3.0.0 CPU：官方预编译包，确保兼容性。
* 静态优先：OpenCV 和依赖（如 freetype）静态链接，运行时仅需少量 Paddle DLL。
* 自动化 CI/CD：Push 到 main 分支时自动触发构建，产物作为 artifact 上传。
* 本地部署友好：生成的 ppocr.exe 可直接在 Windows 机器上运行 OCR 任务。

注意：不支持 Windows XP SP3（PaddleOCR 和 OpenCV 官方不兼容）。


## 先决条件

本地测试环境：

* 操作系统：Windows 7/10/11（x64）。
* 运行时依赖：Visual C++ Redistributable 2019/2022（下载自 Microsoft 官网）。
* 模型文件：需手动下载 PaddleOCR 模型（见使用方法）。

GitHub 仓库

私有仓库：https://github.com/acechat/PaddleOCR-build.git。
启用 GitHub Actions（默认免费）。