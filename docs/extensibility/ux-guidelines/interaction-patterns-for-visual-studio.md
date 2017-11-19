---
title: "互動模式適用於 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e084ace914f65a9e97307f0a70d6c5e2211be55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="interaction-patterns-for-visual-studio"></a>適用於 Visual Studio 的互動模式
## <a name="overview"></a>概觀  
 設計模式中，在一般情況下，是可以套用在解決問題的相似的條件約束一組特定的情況下設計的核心。 功能和系統設計師做為起始點，然後可適用於其特定的情況下使用這些設計模式。  
  
 Visual Studio 的建置新的功能時，應考量的一般互動模式的程式庫。 有兩個核心內容，我們設計模式： Visual Studio 用戶端 (devenv) 與 Visual Studio Online。 針對某些設計問題，沒有都適用於所有情況下的常見模式。 在許多情況下，不過，解決方案可能會不同，要呈現在瀏覽器和裝載於用戶端應用程式的 ui。  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio 用戶端模式類型  
  
|模式類型|說明|範例|  
|------------------|-----------------|--------------|  
|**應用程式層級模式**|應用程式，判斷或顯示應用程式內容，並包含複合和控制項模式，其中通用的高層級模式|工具視窗<br />文件視窗|  
|**複合模式**|常見的模式，可能會跨越多個應用程式模式或由數個不同的組態中的控制項所組成的可辨識的模式|檢視切換<br />-清單產生器<br />顯示資料<br />-通知<br />-驗證<br />選取模型|  
|**控制項模式**|預期的具體說明如何低階控制項的行為|-樹狀檢視<br />編輯方格控制項中|  
  
## <a name="application-patterns"></a>應用程式模式  
 概括而言，Visual Studio 介面包含多個視窗、 對話方塊、 命令和工具列單一 IDE 中。 Visual Studio 階層架構會決定內容及磁碟機的功能表。 在 IDE 的使用者介面的索引鍵的整合點是文件視窗、 工具視窗、 專案、 命令結構、 文字編輯器、 工具箱、 屬性 視窗和工具 > 選項。  
  
 有的每一個使用者介面中重要的整合點，在 IDE 的基本的使用模式：  
  
-   [適用於 Visual Studio 的功能表和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [視窗互動](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [工具視窗](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [文件編輯器慣例](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [專案](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>常見的控制項模式  
 控制項模式主要是有關如何個別控制項預期的行為。 這是在其中最重要的一致性是一個區域。  
  
 在 Visual Studio 中最常見的控制項應該遵循 Windows 桌面的指導方針。 我們的指導原則只會包含我們要擴大與 Visual Studio 特定互動或在其中我們取代指導方針完全以調整以符合我們複雜的使用者需求的 Visual Studio 的地方的常見慣例的區域。  
  
-   [適用於 Visual Studio 的通用控制項模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [通用控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>複合模式  
 有數種方式來完成工作所預期的使用者。 可能的情況下，功能應該設計成可使用這些模式進行互動和視覺化設計。  
  
 雖然還有許多的複合模式，在 Visual Studio 中，部分最重要的一致性就是：  
  
-   [適用於 Visual Studio 的複合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [物件在 UI 中和其內](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [選擇模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [持續性和儲存設定](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [觸控輸入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)