---
title: Visual Studio 的互動模式 |Microsoft Docs
description: 瞭解您在建立 Visual Studio 的新功能時，可以使用的常見互動模式程式庫。
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900547"
---
# <a name="interaction-patterns-for-visual-studio"></a>適用於 Visual Studio 的互動模式
## <a name="overview"></a>概觀
 一般而言，設計模式是一種設計的核心，可在特定情況下套用，以解決類似條件約束集的問題。 功能和系統設計工具會使用這些設計模式作為起點，然後調整為其特定情況。

 Visual Studio 具有在建立新功能時應考慮的常見互動模式程式庫。 我們的設計模式有兩個核心內容： Visual Studio 用戶端 (devenv) 和 GitHub Codespaces (先前 Visual Studio Online) 。 針對某些設計問題，有一個可在所有情況下都能順利運作的通用模式。 不過，在許多情況下，對於在瀏覽器中顯示且裝載于用戶端應用程式的 UI 而言，解決方案可能會有所不同。

### <a name="visual-studio-client-pattern-types"></a>Visual Studio 用戶端模式類型

|模式類型|描述|範例|
|------------------|-----------------|--------------|
|**應用層級模式**|應用程式通用的高階模式、判斷或顯示應用程式內容，並在其中包含複合和控制項模式|-工具視窗<br />-文件視窗|
|**複合模式**|可能橫跨應用程式模式的常見模式，或在不同設定中由數個控制群組成的可辨識模式|-View 切換<br />-清單產生器<br />-顯示資料<br />-通知<br />-驗證<br />-選取模型|
|**控制項模式**|如何預期低層級控制項的行為相關細節|-樹狀檢視<br />-在方格控制項內編輯|

## <a name="application-patterns"></a>應用程式模式
 概括而言，Visual Studio 介面是由單一 IDE 內的多個視窗、對話方塊、命令和工具列所組成。 Visual Studio 階層會決定內容和磁片磁碟機功能表。 IDE 使用者介面中的主要整合點是 [檔視窗]、[工具視窗]、[專案]、[命令結構]、[文字編輯器]、[工具箱]、[屬性視窗] 和 [工具] > 選項。

 在 IDE 的使用者介面中，每個主要整合點都有基本的使用模式：

- [適用於 Visual Studio 的功能表和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [視窗互動](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [工具視窗](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [檔編輯器慣例](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [專案](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>通用控制項模式
 控制項模式主要是關於如何預期個別控制項的行為。 這是一致性最重要的一個區域。

 Visual Studio 中的最常見控制項應遵循桌面 Windows 指導方針。 我們的指導方針只包含需要以 Visual Studio 特定互動增強常見慣例的領域，或是我們完全取代指導方針以量身打造 Visual Studio 以符合複雜使用者需求的地方。

- [適用於 Visual Studio 的通用控制項模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [通用控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>複合模式
 有幾種方式可讓使用者完成工作。 在可能的情況下，功能應該設計為使用這些模式來進行互動和視覺化設計。

 雖然 Visual Studio 內有許多複合模式，但對一致性而言最重要的部分如下：

- [適用於 Visual Studio 的複合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [物件內部 UI 和查看](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [選取模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [持續性和儲存設定](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [觸控輸入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
