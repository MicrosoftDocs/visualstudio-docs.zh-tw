---
title: 適用於 Visual Studio 的互動模式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0a25eac1c14c1d07096840b88a1ec63593f56
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824306"
---
# <a name="interaction-patterns-for-visual-studio"></a>適用於 Visual Studio 的互動模式
## <a name="overview"></a>總覽
 設計模式中，在一般情況下，是一種設計，可以套用在特定情況下使用相似的條件約束一組解決問題的核心。 功能和系統設計工具會使用這些設計模式，作為起始點，然後可適用於其特定的情況。

 Visual Studio 的建置新的功能時，應考量的一般互動模式的程式庫。 有兩個核心內容，我們的設計模式：Visual Studio 用戶端 (devenv) 和 Visual Studio Online。 針對某些設計問題，沒有適用於所有情況下的通用模式。 在許多情況下，不過，解決方案可能會不同的瀏覽器，以及可裝載於用戶端應用程式內顯示的 ui。

### <a name="visual-studio-client-pattern-types"></a>Visual Studio 用戶端模式類型

|模式類型|說明|範例|
|------------------|-----------------|--------------|
|**應用程式層級模式**|一般應用程式，判斷或顯示應用程式內容，並包含在其中的複合和控制項模式的高階模式|-工具視窗<br />-文件視窗|
|**複合模式**|常見的模式，可能會跨越應用程式模式或在不同的組態中的數個控制項所組成的可辨識的模式|檢視切換<br />清單產生器<br />-顯示資料<br />-通知<br />-驗證<br />選取模型|
|**控制項模式**|關於如何低層級的控制項的細節預期的行為|-樹狀檢視<br />編輯中的方格控制項|

## <a name="application-patterns"></a>應用程式模式
 概括而言，Visual Studio 介面會包含多個視窗、 對話方塊、 命令及單一 IDE 中的工具列。 Visual Studio 階層架構決定內容及磁碟機的功能表。 IDE 的使用者介面的重要的整合點是文件視窗、 工具視窗、 專案、 命令結構、 文字編輯器、 工具箱、 屬性 視窗中及工具 > 選項。

 有每個使用者介面中重要的整合點，在 IDE 的基本使用方式模式：

- [適用於 Visual Studio 的功能表和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [視窗的互動](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [工具視窗](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [文件編輯器慣例](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [專案](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>常見的控制項模式
 控制項模式主要是有關如何個別控制項預期行為。 這是在其中一致性是最重要的其中一個區域。

 Visual Studio 中的最常見控制項應該遵循的桌面 Windows 指導方針。 我們的指導方針只包含我們要擴大與 Visual Studio 特定的互動或在其中我們取代指導方針完全以調整以符合我們的資深使用者需求的 Visual Studio 的地方的常見慣例的區域。

- [適用於 Visual Studio 的通用控制項模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [通用控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>複合模式
 有數種方式來完成工作的使用者預期。 可能的話，功能應可使用這些模式的互動和視覺化設計。

 雖然有許多的複合模式，在 Visual Studio 中一些最重要的方面的一致性是：

- [適用於 Visual Studio 的複合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [物件上 UI 和預覽](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [選取項目模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [持續性和儲存設定](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [具備觸控輸入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
