---
title: WPF MSBuild 工作參考 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630843"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild 工作參考

Windows Presentation Foundation (WPF) 建置程序會擴充 Microsoft Build Engine (MSBuild) 增加一組建置工作，包括編譯標記和處理資源的工作。

## <a name="in-this-section"></a>本節內容

- [FileClassifier](../msbuild/fileclassifier-task.md)

 將一組來源資源分類為將內嵌至組件的來源資源。 如果無法將資源當地語系化，即會將它內嵌至主應用程式組件；否則，會將它內嵌至附屬組件。

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 如果專案中至少有一個 XAML 頁引用在該專案中本地聲明的類型，則生成程式集。 建置流程完成之後，或如果建置流程失敗，都會將產生的組件移除。

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 返回當前 .NET 框架運行時的目錄。

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 將不可當地語系化的 XAML 專案檔案轉換為編譯的二進位格式。

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 對引用同一專案中類型的 XAML 檔執行二次標記編譯。

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 將一個或多個 XAML 二進位格式檔的當地語系化屬性和注釋合併到整個程式集的單個檔中。

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 將一個或多個資源（.jpg、.ico、.bmp、二進位格式的 XAML 和其他擴展類型）嵌入到 *.resources*檔中。* * *.ico* *.bmp*

- [UidManager](../msbuild/uidmanager-task.md)

 檢查、更新或刪除唯一識別碼 （UiD）， 以便當地語系化源 XAML 檔中包含的所有 XAML 元素。

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 在生成 XAML 瀏覽器應用程式 （XBAP） 專案時，將**\<主機InBrowser />** 元素添加到應用程式清單（*\<專案名稱>.exe.manifest）。*

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)