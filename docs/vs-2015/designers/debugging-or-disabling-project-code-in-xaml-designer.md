---
title: 偵錯或停用 XAML 設計工具的專案程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: efb8c943607b4e29c05a2540ee277a90fc57f797
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491736"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>偵錯或停用 XAML 設計工具的專案程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在許多情況下，當應用程式在設計工具中執行時，專案程式碼嘗試存取會傳回不同值或以不同方式運作的屬性或方法，造成 XAML 設計工具發生未處理的例外狀況。 您可以偵錯 Visual Studio 另一個執行個體的專案程式碼，解決這些例外狀況；或暫時停用設計工具中的專案程式碼，防止這些例外狀況發生。  
  
 專案程式碼包括：  
  
-   自訂控制項和使用者控制項  
  
-   類別庫  
  
-   值轉換器  
  
-   標的為從專案程式碼產生之設計階段資料的繫結  
  
 當專案程式碼停用後，Visual Studio 會顯示不再提供資料之繫結的預留位置 (如屬性名稱)，或不再執行之控制項的預留位置。  
  
 ![未處理的例外狀況對話方塊](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>判斷專案程式碼是否會造成例外狀況  
  
1.  在未處理的例外狀況對話方塊中，選擇 [按一下此處可重新載入設計工具]  連結。  
  
2.  在功能表列上選擇 [偵錯] 和 [開始偵錯]  ，以建置及執行應用程式。  
  
     如果應用程式順利建置並執行，則設計階段的例外狀況可能是由在設計工具中執行的專案程式碼所造成。  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>偵錯在設計工具中執行的專案程式碼  
  
1.  在未處理的例外狀況對話方塊中，選擇 [按一下此處可停用執行中的專案程式碼並重新載入設計工具]  連結。  
  
2.  在 [Windows 工作管理員] 中，選擇 [結束工作]  按鈕關閉 Visual Studio XAML 設計工具目前執行的所有執行個體。  
  
     ![TaskManager 中的 XAML 設計工具執行個體](../designers/media/xaml-taskmanager.png "XAML_TaskManager")  
  
3.  在 Visual Studio 中開啟包含要偵錯之程式碼或控制項的 XAML 頁面。  
  
4.  開啟 Visual Studio 的新執行個體，然後開啟您專案的第二個執行個體。  
  
5.  設定專案程式碼的中斷點。  
  
6.  在 Visual Studio 新執行個體的功能表上，選擇 [偵錯] 、[附加至處理序] 。  
  
7.  在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，選擇 [XDesProc.exe] ，然後選擇 [附加]  按鈕。  
  
     ![XAML 設計工具處理序](../designers/media/xaml-attach.png "XAML_Attach")  
  
     這是 Visual Studio 第一個執行個體的 XAML 設計工具處理序。  
  
8.  在 Visual Studio 第一個執行個體的功能表列上，選擇 [偵錯] 和 [開始偵錯] 。  
  
     您現在可以進入正在設計工具中執行的程式碼。  
  
#### <a name="to-disable-project-code-in-the-designer"></a>停用設計工具中的專案程式碼  
  
-   在未處理的例外狀況對話方塊中，選擇 [按一下此處可停用執行中的專案程式碼並重新載入設計工具]  連結。  
  
-   或者，在 XAML 設計工具的工具列上選擇 [停用專案程式碼]  按鈕。  
  
     ![[停用專案程式碼] 按鈕](../designers/media/xaml-disablecode.png "XAML_DisableCode")  
  
     您可以再次切換按鈕重新啟用專案程式碼。  
  
    > [!NOTE]
    >  至於以 ARM 或 X64 處理器為目標的專案，Visual Studio 無法在設計工具中執行專案程式碼，所以停用設計工具中的 [停用專案程式碼]  按鈕。  
  
-   無論哪個選項都會導致重新載入設計工具，然後停用所有相關聯專案的程式碼。  
  
    > [!NOTE]
    >  停用專案程式碼會導致設計階段資料遺失。 另一個方法是偵錯在設計工具中執行的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../designers/designing-xaml-in-visual-studio.md)





