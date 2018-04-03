---
title: 專案和方案檔類型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d239a5e129f12c4521ba190674d84430f8f2e646
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="project-and-solution-file-types"></a>專案和方案檔類型

Visual Studio 支援許多檔案類型。 在特定的安裝中，已安裝的元件決定可支援的檔案類型。 本主題列出在某些一般安裝中支援的方案和專案檔類型。

## <a name="solution-files-sln-and-suo"></a>方案檔 (.sln 和 .suo)

Visual Studio 使用兩種檔案類型 (.sln 和 .suo) 來儲存方案的設定。 這些檔案 (統稱為方案檔) 為方案總管提供了顯示管理檔案的圖形介面所需的資訊。

|副檔名|名稱|描述|
|---------------|----------|-----------------|
|.sln|Visual Studio 方案|將專案、專案項目和方案項目組織到方案中。|
|.suo|方案使用者選項|記錄您對 Visual Studio 進行的使用者層級自訂，例如中斷點。|

## <a name="project-files"></a>專案檔

專案可以包含許多不同的檔案類型。 例如，C# 程式碼檔案的副檔名為 **.cs**，而 C++ 檔案的副檔名為 **.cpp**。 資源儲存在 **.resx** 檔案中，而 XAML 儲存在 **.xaml** 檔案中。 [App.config](../../ide/managing-application-settings-dotnet.md) 檔案包含不應包含在應用程式程式碼中的應用程式資訊，例如連接字串。

如需 C++ 專案檔案類型的詳細資訊，請參閱[為 Visual C++ 專案建立的檔案類型](/cpp/ide/file-types-created-for-visual-cpp-projects)。

## <a name="see-also"></a>另請參閱

[專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)