---
title: "在本機電腦上執行 UWP 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 63cb81c9bc168ad0bda8d675c0bf0bbde3759eff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>在本機電腦上執行的 UWP 應用程式
![僅適用於 Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 若要偵錯、 測試或執行的 UWP 應用程式效能分析，您可以執行應用程式在相同電腦上裝載 Visual Studio。 如果裝置上的顯示器具有觸控功能，則可以執行應用程式的完整功能；否則，只能使用滑鼠和鍵盤手勢。  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>如何在本機電腦上執行  
 若要執行應用程式在本機電腦上，選取**本機**從偵錯工具上的 [開始偵錯] 按鈕旁邊的下拉式清單**標準**工具列。  
  
 ![在本機電腦上執行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 如果您看**標準**工具列上，按一下 **檢視**功能表上，指向**工具列**，然後按一下 **標準**。  
  
 您在下拉式清單中選擇的項目會持續保留在專案屬性檔案中，並成為預設執行目標。  
  
 您也可以直接在專案屬性檔案中設定執行目標。 以滑鼠右鍵按一下專案名稱中的**方案總管] 中**，然後選擇 [**屬性**。 然後，執行下列其中一項：  
  
-   在 C# 和 Visual Basic 專案中，按一下 **偵錯**，然後選取 **本機**從**目標裝置**下拉式清單。  
  
     ![& #35。和 Visual Basic 專案屬性頁](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   在 c + + 和 JavaScript 專案中，展開 **組態屬性**節點中，按一下 **偵錯**，然後選取**本機偵錯工具**從**偵錯工具若要啟動**清單。  
  
     ![C# 43; &#43;和 JavaScript 專案屬性 頁面](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  