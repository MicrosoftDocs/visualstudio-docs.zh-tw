---
title: WPF MSBuild 工作參考 | Microsoft Docs
description: 請參閱 Windows Presentation Foundation (WPF) 組建流程的工作參考，它會擴充 MSBuild 與其他工作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94050565e6c5619781434c7a18307bfbf80b51f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933670"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild 工作參考

Windows Presentation Foundation (WPF) 建置程序會擴充 Microsoft Build Engine (MSBuild) 增加一組建置工作，包括編譯標記和處理資源的工作。

## <a name="in-this-section"></a>本節內容

- [FileClassifier](../msbuild/fileclassifier-task.md)

 將一組來源資源分類為將內嵌至組件的來源資源。 如果無法將資源當地語系化，即會將它內嵌至主應用程式組件；否則，會將它內嵌至附屬組件。

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 如果專案中至少有一個 XAML 頁面參考該專案中本機宣告的類型，則會產生元件。 建置流程完成之後，或如果建置流程失敗，都會將產生的組件移除。

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 傳回目前 .NET Framework 執行時間的目錄。

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 將不可當地語系化的 XAML 專案檔案轉換為編譯的二進位格式。

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 在參考相同專案中類型的 XAML 檔案上執行第二階段標記編譯。

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 將一或多個 XAML 二進位格式檔案的當地語系化屬性和批註，合併成整個元件的單一檔案。

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 將一或多個資源內嵌 (*.jpg*、 *.ico*、 *.Bmp*、二進位格式的 XAML，以及其他擴充類型) 至 *.resources* 檔。

- [UidManager](../msbuild/uidmanager-task.md)

 檢查、更新或移除 (Uid) 的唯一識別碼，以當地語系化來源 XAML 檔案中包含的所有 XAML 專案。

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 **\<hostInBrowser />** 在建立 XAML 瀏覽器應用程式 (XBAP) 專案時，將專案新增至應用程式資訊清單 (*\<projectname> .exe. 指令* 清單) 。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)