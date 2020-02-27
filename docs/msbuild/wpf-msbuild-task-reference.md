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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630843"
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

 將不可當地語系化的 XAML 專案檔案轉換成編譯的二進位格式。

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 在參考相同專案中類型的 XAML 檔案上執行第二階段標記編譯。

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 將一或多個 XAML 二進位格式檔案的當地語系化屬性和批註，合併成整個元件的單一檔案。

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 將一或多個資源（ *.jpg*、 *.ico*、 *.Bmp*、二進位格式的 XAML，以及其他副檔名類型）內嵌到 *.resources*檔案中。

- [UidManager](../msbuild/uidmanager-task.md)

 檢查、更新或移除唯一識別碼（Uid），以將來源 XAML 檔案中包含的所有 XAML 元素當地語系化。

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 建立 XAML 瀏覽器應用程式（XBAP）專案時，將 **\<hostInBrowser/>** 元素新增至應用程式資訊清單（ *\<專案名稱 >. .exe. manifest*）。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)