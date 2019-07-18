---
title: 在本機電腦上的執行 Windows 市集應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196334"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>在本機電腦上執行 Windows 市集應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

僅適用於 Windows] (../Image/windows_only_content.png"windows_only_content")  
  
 若要偵錯、測試或執行 Windows 市集應用程式的效能分析，您可以在裝載 Visual Studio 的相同電腦上執行應用程式。 如果裝置上的顯示器具有觸控功能，則可以執行應用程式的完整功能；否則，只能使用滑鼠和鍵盤手勢。  
  
## <a name="BKMK_In_this_topic"></a>本主題內容  
 您將學習：  
  
 [如何在本機電腦上執行](#BKMK_How_to_run_on_a_local_machine)  
  
 [如何在單一監視器上切換 Windows 市集應用程式和 Visual Studio](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="BKMK_How_to_run_on_a_local_machine"></a> 如何在本機電腦上執行  
 若要在本機電腦上執行應用程式，請選取**本機電腦**從偵錯工具上的 [開始偵錯] 按鈕旁邊下拉式清單**標準**工具列。  
  
 ![在本機電腦上執行](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 如果您看**標準**工具列上，按一下**檢視**功能表上，指向**工具列**，然後按一下**標準**。  
  
 您在下拉式清單中選擇的項目會持續保留在專案屬性檔案中，並成為預設執行目標。  
  
 您也可以直接在專案屬性檔案中設定執行目標。 中的專案名稱上按一下滑鼠右鍵**方案總管**，然後選擇**屬性**。 然後，執行下列其中一項：  
  
- 在 C# 和 Visual Basic 專案中，按一下**偵錯**，然後選取**本機**從**目標裝置**下拉式清單。  
  
     ![C&#35;和 Visual Basic 專案屬性頁](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- 在C++JavaScript 專案中，展開**組態屬性**節點，按一下 **偵錯**，然後選取**本機偵錯工具**從**若要啟動的偵錯工具**清單。  
  
     ![C&#43; &#43;和 JavaScript 專案屬性頁](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> 如何在單一監視器上切換 Windows 市集應用程式和 Visual Studio  
 **若要從執行個體的 Windows 市集應用程式切換至 Visual Studio**  
  
 如果您在本機電腦上執行 Windows 市集應用程式，而且只使用單一監視器，則可能會想要切換回 Visual Studio，同時讓應用程式繼續執行。 例如，應用程式可能處於中斷點無法到達的狀態 (例如，等待某個事件，或陷入冗長或無止盡的迴圈中)。 若要返回 Visual Studio，請按 ALT + TAB。
