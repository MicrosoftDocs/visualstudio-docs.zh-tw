---
title: "一般專案屬性 (Android C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.openlocfilehash: f564ca09b3a19848ae95128ba8b529b8a84c2210
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="general-project-properties-android-c"></a>一般專案屬性 (Android C++)

屬性 | 說明 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑；可包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑；可包含環境變數。
目標名稱 | 指定這個專案將會產生的檔名。
目標副檔名 | 指定這個專案將會產生的副檔名。 (例如 .exe 或 .dll)
清除時要刪除的副檔名 | 清除或重建時中繼目錄中要刪除的檔案。檔案名稱以萬用字元表示，項目之間以分號區隔。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
平台工具組 | 指定用於建置目前組態的工具組；如果未設定，則使用預設工具組。
組態類型 | 指定此組態所產生的輸出類型。 | **動態程式庫 (.so)** - 動態程式庫 (.so)<br>**靜態程式庫 (.a)** - 靜態程式庫 (.a)<br>**公用程式** - 公用程式<br>**Makefile** - Makefile<br>
目標 API 層級 | 這個組態的目標 Android NDK API 層級。
STL 的使用 | 指定要用於這個組態的 C++ 標準程式庫。 | **最小 C++ 執行階段程式庫 (系統)**<br>**C++ 執行階段靜態程式庫 (gabi++_static)**<br>**C++ 執行階段共用程式庫 (gabi++_shared)**<br>**STLport 執行階段靜態程式庫 (stlport_static)**<br>**STLport 執行階段共用程式庫 (stlport_shared)**<br>**GNU STL 靜態程式庫 (gnustl_static)**<br>**GNU STL 共用程式庫 (gnustl_shared)**<br>**LLVM libc++ 靜態程式庫 (c++_static)**<br>**LLVM libc++ 共用程式庫 (c++_shared)**<br>
Thumb 模式 | 產生為 Thumb 微架構所執行的程式碼。 這僅適用於 ARM 架構。 | **Thumb**<br>**ARM**<br>**已停用**<br>
