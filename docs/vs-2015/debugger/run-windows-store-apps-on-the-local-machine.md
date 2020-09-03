---
title: 在本機電腦上執行 Windows Store 應用程式 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196334"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>在本機電腦上執行 Windows 市集應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

僅適用于 Windows] (。/Image/windows_only_content.png "windows_only_content" )   
  
 若要偵錯、測試或執行 Windows 市集應用程式的效能分析，您可以在裝載 Visual Studio 的相同電腦上執行應用程式。 如果裝置上的顯示器具有觸控功能，則可以執行應用程式的完整功能；否則，只能使用滑鼠和鍵盤手勢。  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 本主題中  
 您將學習：  
  
 [如何在本機電腦上執行](#BKMK_How_to_run_on_a_local_machine)  
  
 [如何在單一監視器上切換 Windows 市集應用程式與 Visual Studio](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> 如何在本機電腦上執行  
 若要在本機電腦上執行應用程式，請從偵錯工具 [**標準**] 工具列上 [開始偵錯工具] 按鈕旁的下拉式清單中選取 [**本機電腦**]。  
  
 ![執行於本機電腦](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 如果您看不到 [ **標準** ] 工具列，請按一下 [ **流覽** ] 功能表，指向 [ **工具列**]，然後按一下 [ **標準**]。  
  
 您在下拉式清單中選擇的項目會持續保留在專案屬性檔案中，並成為預設執行目標。  
  
 您也可以直接在專案屬性檔案中設定執行目標。 在 **方案總管** 中的專案名稱上按一下滑鼠右鍵，然後選擇 [ **屬性**]。 然後，執行下列其中一項：  
  
- 在 c # 和 Visual Basic 專案中，按一下 [ **Debug** ]，然後從 [**目標裝置**] 下拉式清單中選取 [**本機電腦**]。  
  
     ![C&#35; 和 Visual Basic 專案屬性頁](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- 在 c + + 和 JavaScript 專案中，展開 [設定**屬性**] 節點，按一下 [**調試**程式]，然後從**偵錯工具啟動**清單中選取 [**本機偵錯工具**]。  
  
     ![C&#43;&#43; 和 JavaScript 專案屬性頁面](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> 如何在單一監視器上切換 Windows Store 應用程式和 Visual Studio  
 **從執行中的 Windows 市集應用程式執行個體切換至 Visual Studio**  
  
 如果您在本機電腦上執行 Windows 市集應用程式，而且只使用單一監視器，則可能會想要切換回 Visual Studio，同時讓應用程式繼續執行。 例如，應用程式可能處於中斷點無法到達的狀態 (例如，等待某個事件，或陷入冗長或無止盡的迴圈中)。 若要返回 Visual Studio，請按 ALT + TAB。
