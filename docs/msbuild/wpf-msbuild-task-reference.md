---
title: WPF MSBuild 工作參考 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30acdaddc132a40c37bc489b07ae3b7f2843b215
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild 工作參考
Windows Presentation Foundation (WPF) 建置程序會擴充 Microsoft Build Engine (MSBuild) 增加一組建置工作，包括編譯標記和處理資源的工作。  
  
## <a name="in-this-section"></a>本節內容  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 將一組來源資源分類為將內嵌至組件的來源資源。 如果無法將資源當地語系化，即會將它內嵌至主應用程式組件；否則，會將它內嵌至附屬組件。  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 如果專案中有至少一個 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 網頁參考該專案中本機宣告的類型，即產生組件。 建置流程完成之後，或如果建置流程失敗，都會將產生的組件移除。  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 傳回目前 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 執行階段的目錄。  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 將未當地語系化的 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 專案檔轉換成已編譯的二進位格式。  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 在參考相同專案中類型的 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 檔案上執行第二階段標記編譯。  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 將一或多個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化屬性和註解合併到適用於整個組件的單一檔案。  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 將一或多種資源 (.jpg、.ico、.bmp、二進位格式的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 以及其他副檔名類型) 內嵌到 .resources 檔案。  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 檢查、更新或移除唯一識別碼 (UID)，以將來源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案中包含的所有 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 項目當地語系化。  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 建置 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] 專案時，將 **\<hostInBrowser />** 項目新增至應用程式資訊清單 (*projectname*.exe.manifest)。  
  
## <a name="see-also"></a>請參閱  
 [ MSBuild](../msbuild/msbuild.md)