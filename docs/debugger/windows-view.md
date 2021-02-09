---
title: Windows View |Microsoft Docs
description: Windows View 會顯示所有視窗和控制項的樹狀結構。 您可以使用它做為起點來取得感興趣之 windows 的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 34a66e9c2728798330b52f87afe8ecdea8733508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906333"
---
# <a name="windows-view"></a>視窗檢視
當您第一次開啟 Spy + + 時，Windows view 會顯示系統中所有視窗和控制項的樹狀結構。 系統會顯示視窗控制碼和類別名稱。 目前的桌面視窗位於樹狀結構的頂端。 所有其他視窗都是桌面的子系，並根據標準視窗階層列出。 Expansible 清單會以縮排方式顯示在其父代下方的 [同輩] 視窗。

 下圖顯示已展開最上層節點的典型 Spy + + Windows view。

 ![Spy&#43;&#43; Windows View](../debugger/media/spy--_windowsview.png "Spy + + _WindowsView") Spy + + Windows View

 目前的桌面視窗位於樹狀結構的頂端。 所有其他視窗都是桌面的子系，並根據標準視窗階層列出，並以迭置順序排列同輩視窗。 您可以按一下節點旁的 + 或-符號，展開或折迭樹狀結構的任何父節點。

 當 Windows view 具有焦點時，您可以使用 [ [視窗搜尋] 對話方塊](../debugger/window-search-dialog-box.md) 中的 [Finder] 工具，顯示您系統上任何開啟視窗的資訊。

## <a name="in-this-section"></a>本節內容
 [如何：使用 Finder 工具](../debugger/how-to-use-the-finder-tool.md) 顯示此工具如何掃描 windows 中的屬性或訊息。

 [如何：在 Windows View 中搜尋視窗](../debugger/how-to-search-for-a-window-in-windows-view.md) 說明如何在 Windows view 中尋找特定視窗。

 [如何：顯示視窗屬性](../debugger/how-to-display-window-properties.md) m 程式以開啟視窗屬性對話方塊。

## <a name="related-sections"></a>相關章節
 [Spy + + Views](../debugger/spy-increment-views.md) 說明 windows、訊息、進程和執行緒的 Spy + + 樹狀檢視。

 [使用 Spy + +](../debugger/using-spy-increment.md) 介紹 Spy + + 工具，並說明其使用方式。

 [尋找視窗對話方塊](../debugger/find-window-dialog-box.md) 用來從特定視窗中查看屬性或訊息。

 [[視窗搜尋] 對話方塊](../debugger/window-search-dialog-box.md)用來尋找 Windows view 中特定視窗的節點。

 [視窗屬性對話方塊](../debugger/window-properties-dialog-box.md) 用來顯示在 Windows view 中選取之視窗的屬性。

 [Spy + + 參考](../debugger/spy-increment-reference.md) 包含描述每個 Spy + + 功能表和對話方塊的章節。