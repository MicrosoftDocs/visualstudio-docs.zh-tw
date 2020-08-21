---
title: 'Visual Studio 檔：2020年7月的新功能 '
titleSuffix: ''
description: 2020年7月 Visual Studio 檔中的新功能。
ms.date: 08/06/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: f8f5ac8944120d5a48ab0f199d19376423abd2eb
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714416"
---
# <a name="visual-studio-docs-whats-new-in-the-docs-for-july-2020"></a>Visual Studio 檔：2020年7月檔的新功能

歡迎使用2020年7月 Visual Studio 檔中的新功能。 本文列出在這段期間內檔的一些主要變更。

## <a name="code-quality"></a>程式碼品質

**新文章**

- [CA1417：不要 `OutAttribute` 在 P/invoke 的字串參數上使用](/visualstudio/code-quality/ca1417) -新增 CA1417 的檔
- [CA1805：不必要初始化。](/visualstudio/code-quality/ca1805) -新增適用于 CA1805 的檔
- [CA1836：在可用時優先使用 IsEmpty 計數](/visualstudio/code-quality/ca1836) -新增 CA1836 的檔 (偏好 IsEmpty 超過計數) 
- [CA2016：將 CancellationToken 參數轉寄至採用一](/visualstudio/code-quality/ca2016) 份檔 CA2016 的方法-將 CancellationToken 參數轉寄至採用一個
- [CA2350：確定 DataTable. ReadXml ( # A1's 輸入是受信任](/visualstudio/code-quality/ca2350) 的-初始資料集/DataTable 還原序列化規則檔
- [CA2351：確定資料集 ReadXml ( # A1's 輸入是受信任](/visualstudio/code-quality/ca2351) 的-初始資料集/DataTable 還原序列化規則檔
- [CA2352：可序列化類型中 Unsafe 的資料集或 DataTable 可能很容易遭受遠端程式碼執行攻擊](/visualstudio/code-quality/ca2352) -初始資料集/DataTable 還原序列化規則檔
- [CA2353： serializable 類型中不安全的資料集或 datatable](/visualstudio/code-quality/ca2353) -初始資料集/DataTable 還原序列化規則檔
- [CA2354：還原序列化的物件圖形中不安全的資料集或 DataTable 可能易受遠端程式碼執行攻擊](/visualstudio/code-quality/ca2354) -初始資料集/DataTable 還原序列化規則檔
- [CA2355：還原序列化的物件圖形中不安全的資料集或 datatable](/visualstudio/code-quality/ca2355) -初始資料集/DataTable 還原序列化規則檔
- [CA2356： web 還原序列化物件圖形中不安全的資料集或 datatable 類型](/visualstudio/code-quality/ca2356) -初始資料集/DataTable 還原序列化規則檔

## <a name="containers"></a>容器

**新文章**

- 使用 Kubernetes： yaml[設定以 Kubernetes-Local Process 設定本機進程](/visualstudio/containers/configure-local-process-with-kubernetes)
- [使用本機進程搭配 Kubernetes (預覽) ](/visualstudio/containers/local-process-kubernetes) -開發人員空間遷移
- [本機處理序與 Kubernetes 搭配使用的方式](/visualstudio/containers/overview-local-process-kubernetes)
  - Kubernetes 的本機進程：新增路由區段
  - 開發人員空間遷移

## <a name="cross-platform"></a>跨平台

**更新的文章**

- [變更 log (Visual Studio Tools for Unity，Windows) ](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity) 將 VSTU 變更記錄至4.7.1。0
- [變更 Log (Visual Studio Tools for Unity、Mac) ](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity-mac) 將 VSTUM 變更記錄至2.7.1。0

## <a name="get-started"></a>開始使用

**新文章**

- [教學課程：擴充簡單的 c # 主控台應用程式](/visualstudio/get-started/csharp/tutorial-console-part-2) -發行延伸人行道教學課程第一版

## <a name="ide"></a>IDE

**新文章**

- [開發人員社群指導方針](/visualstudio/ide/developer-community-guidelines) -新增 DevCom 指導方針
- [未匯入類型和擴充方法的 IntelliSense 完成](/visualstudio/ide/reference/intellisense-completion-unimported-types-extension-methods)

## <a name="install"></a>安裝

**新文章**

- [使用基本離線配置更新 Visual Studio](/visualstudio/install/update-minimal-layout) -檔基本版面配置功能
- [Visual Studio enterprise 指南](/visualstudio/install/visual-studio-enterprise-guide) -企業指南

## <a name="javascript"></a>JavaScript

**新文章**

- [編譯 typescript 程式碼 ( # A0) ](/visualstudio/javascript/compile-typescript-code-npm) -TypeScript 編譯和組建
- [編譯 typescript 程式碼 (ASP.NET Core) ](/visualstudio/javascript/compile-typescript-code-nuget) -TypeScript 編譯和組建

## <a name="msbuild"></a>MSBuild

**新文章**

- [一般 msbuild 專案中繼資料](/visualstudio/msbuild/common-msbuild-item-metadata) -MSBuild：使用連結和程式庫新增選擇性中繼資料的資料表
- [Msbuild 中的方案篩選](/visualstudio/msbuild/solution-filters) -msbuild 方案篩選

## <a name="test"></a>測試

**新文章**

- [使用 Test explorer 來偵測及分析單元測試](/visualstudio/test/debug-unit-tests-with-test-explorer) -test explorer 效能工作

**更新的文章**

- [使用 *.runsettings* 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - 使用 .runsettings 檔案設定單元測試的更新
  - 變更了操作說明的選項，並新增了範例。

## <a name="community-contributors"></a>社群參與者

下列人員會在這段期間內參與 Visual Studio 檔。 感謝您！ 遵循《 [參與者指南》](https://docs.microsoft.com/contribute/)中的指導方針，瞭解如何參與 Visual Studio 檔。

- [briuk](https://github.com/briuk) -Viktor Briukhanov (2) 
- [Youssef1313](https://github.com/Youssef1313) -Youssef Victor (2) 
- [ArntWork](https://github.com/ArntWork) -Legolas (1) 
- [Asugakoisi](https://github.com/Asugakoisi) -アスガコイシ (1) 
- [Delizald](https://github.com/Delizald) -David Elizalde (1) 
- [farisachugthai](https://github.com/farisachugthai) -Faris Chugthai (1) 
- [mycalingram](https://github.com/mycalingram) -Mycal (1) 
- [tuyen-工作](https://github.com/tuyen-at-work) -tuyen Pham (1) 
