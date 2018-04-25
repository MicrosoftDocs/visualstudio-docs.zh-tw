---
title: Clang 連結器屬性 (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 3611268c17d26328d131eacafb92b1ce55c7d07f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="clang-linker-properties-android-c"></a>Clang 連結器屬性 (Android C++)

屬性 | 描述 | 選擇
--- | ---| ---
輸出檔案 | 此選項會覆寫連結器所建立之程式的預設名稱和位置。 (-o)
顯示進度 | 列印連結器進度訊息。
版本 | -version 選項會指示連結器將版本號碼置於可執行檔的標頭中。
啟用詳細資訊輸出 | -verbose 選項會指示連結器輸出詳細訊息以供偵錯之用。
啟用累加連結 | 此選項會指示連結器啟用累加連結。
共用程式庫搜尋路徑 | 允許使用者填入共用程式庫搜尋路徑。
其他程式庫目錄 | 允許使用者覆寫環境程式庫路徑。 (-L folder)。
回報未解析的符號參考 | 啟用此選項時，會回報未解析的符號參考。
最佳化記憶體的使用 | 視需要重新讀取符號表，最佳化記憶體的使用。
忽略特定的預設程式庫 | 指定要忽略的一或多個預設程式庫名稱。
強制符號參考 | 強制在輸出檔案中將符號輸入為未定義的符號。
偵錯工具符號資訊 | 來自輸出檔中的偵錯工具符號資訊。 | **包含全部**<br>**省略不需要的符號以重新配置處理**<br>**僅省略偵錯工具符號資訊**<br>**省略所有符號資訊**<br>
封裝偵錯工具符號資訊 | 封裝之前刪除偵錯工具符號資訊。  將會使用原始的二進位檔複本進行偵錯。
對應檔案名稱 | Map 選項會指示連結器以使用者指定的名稱來建立對應檔案。
重新配置之後將變數標記為唯讀 | 此選項會在重新配置之後，將變數標記為唯讀。
啟用立即函式繫結 | 此選項會將物件標記為要立即進行函式繫結。
需要可執行檔堆疊 | 此選項會將輸出標記為不需要可執行檔堆疊。
Whole Archive | Whole Archive 會使用來自來源及其他相依性的所有程式碼。
其他選項 | 其他選項。
其他相依性 | 指定要新增至連結命令列的其他項目。
程式庫相依性 | 此選項可指定要新增至連結器命令列的其他程式庫。 其他程式庫會新增至連結器命令列的結尾，並以 'lib' 為開頭，以 '.a' 或 '.so' 副檔名結尾。  (-lFILE)
