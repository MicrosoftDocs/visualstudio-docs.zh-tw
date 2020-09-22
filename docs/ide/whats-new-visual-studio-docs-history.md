---
title: 'Visual Studio 檔：新功能的歷程記錄 '
titleSuffix: ''
description: Visual Studio 文件中的新功能歷程記錄
ms.date: 09/01/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809462"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Visual Studio 文件中的新功能歷程記錄

歡迎使用 Visual Studio 檔的新功能歷程記錄。本主題包含2020年8月之前的檔的重大變更 (從2020年7月) 開始。 如需最新的新功能，請參閱 [Visual Studio 檔：檔中的新功能](whats-new-visual-studio-docs.md)。

## <a name="july-2020"></a>2020 年 7 月
### <a name="code-quality"></a>程式碼品質

**新文章**

- [CA1417：不要 `OutAttribute` 在 P/invoke 的字串參數上使用](../code-quality/ca1417.md) -新增 CA1417 的檔
- [CA1805：不必要初始化。](../code-quality/ca1805.md) -新增適用于 CA1805 的檔
- [CA1836：在可用時優先使用 IsEmpty 計數](../code-quality/ca1836.md) -新增 CA1836 的檔 (偏好 IsEmpty 超過計數) 
- [CA2016：將 CancellationToken 參數轉寄至採用一](../code-quality/ca2016.md) 份檔 CA2016 的方法-將 CancellationToken 參數轉寄至採用一個
- [CA2350：確定 DataTable. ReadXml ( # A1's 輸入是受信任](../code-quality/ca2350.md) 的-初始資料集/DataTable 還原序列化規則檔
- [CA2351：確定資料集 ReadXml ( # A1's 輸入是受信任](../code-quality/ca2351.md) 的-初始資料集/DataTable 還原序列化規則檔
- [CA2352：可序列化類型中 Unsafe 的資料集或 DataTable 可能很容易遭受遠端程式碼執行攻擊](../code-quality/ca2352.md) -初始資料集/DataTable 還原序列化規則檔
- [CA2353： serializable 類型中不安全的資料集或 datatable](../code-quality/ca2353.md) -初始資料集/DataTable 還原序列化規則檔
- [CA2354：還原序列化的物件圖形中不安全的資料集或 DataTable 可能易受遠端程式碼執行攻擊](../code-quality/ca2354.md) -初始資料集/DataTable 還原序列化規則檔
- [CA2355：還原序列化的物件圖形中不安全的資料集或 datatable](../code-quality/ca2355.md) -初始資料集/DataTable 還原序列化規則檔
- [CA2356： web 還原序列化物件圖形中不安全的資料集或 datatable 類型](../code-quality/ca2356.md) -初始資料集/DataTable 還原序列化規則檔

### <a name="containers"></a>容器

**新文章**

- 使用 Kubernetes： yaml[設定以 Kubernetes-Local Process 設定本機進程](../containers/configure-local-process-with-kubernetes.md)
- [使用本機進程搭配 Kubernetes (預覽) ](../containers/local-process-kubernetes.md) -開發人員空間遷移
- [本機處理序與 Kubernetes 搭配使用的方式](../containers/overview-local-process-kubernetes.md)
  - Kubernetes 的本機進程：新增路由區段
  - 開發人員空間遷移

### <a name="cross-platform"></a>跨平台

**更新的文章**

- [變更 log (Visual Studio Tools for Unity，Windows) ](../cross-platform/change-log-visual-studio-tools-for-unity.md) 將 VSTU 變更記錄至4.7.1。0
- [變更 Log (Visual Studio Tools for Unity、Mac) ](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) 將 VSTUM 變更記錄至2.7.1。0

### <a name="get-started"></a>開始使用

**新文章**

- [教學課程：擴充簡單的 c # 主控台應用程式](../get-started/csharp/tutorial-console-part-2.md) -發行延伸人行道教學課程第一版

### <a name="ide"></a>IDE

**新文章**

- [開發人員社群指導方針](./developer-community-guidelines.md) -新增 DevCom 指導方針
- [未匯入類型和擴充方法的 IntelliSense 完成](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>安裝

**新文章**

- [使用基本離線配置更新 Visual Studio](../install/update-minimal-layout.md) -檔基本版面配置功能
- [Visual Studio enterprise 指南](../install/visual-studio-enterprise-guide.md) -企業指南

### <a name="javascript"></a>JavaScript

**新文章**

- [編譯 typescript 程式碼 ( # A0) ](../javascript/compile-typescript-code-npm.md) -TypeScript 編譯和組建
- [編譯 typescript 程式碼 (ASP.NET Core) ](../javascript/compile-typescript-code-nuget.md) -TypeScript 編譯和組建

### <a name="msbuild"></a>MSBuild

**新文章**

- [一般 msbuild 專案中繼資料](../msbuild/common-msbuild-item-metadata.md) -MSBuild：使用連結和程式庫新增選擇性中繼資料的資料表
- [Msbuild 中的方案篩選](../msbuild/solution-filters.md) -msbuild 方案篩選

### <a name="test"></a>測試

**新文章**

- [使用 Test explorer 來偵測及分析單元測試](../test/debug-unit-tests-with-test-explorer.md) -test explorer 效能工作

**更新的文章**

- [使用 *.runsettings* 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - 使用 .runsettings 檔案設定單元測試的更新
  - 變更了操作說明的選項，並新增了範例。