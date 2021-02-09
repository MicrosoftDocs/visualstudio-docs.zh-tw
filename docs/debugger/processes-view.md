---
title: 進程視圖 |Microsoft Docs
description: '[進程] view 會顯示您系統上所有使用中進程的樹狀結構。 深入瞭解其內容並使用，並遵循其他資訊的連結。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d48be382e222c9ca494237ae6b72bae54bb90d62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891445"
---
# <a name="processes-view"></a>處理序檢視
[進程] 視圖會顯示您系統上所有使用中進程的樹狀結構。 系統會顯示處理序識別碼和模組名稱。 如果您想要檢查特定的系統進程（通常會對應至執行中的程式），請使用 [進程]。 系統會以模組名稱來識別處理常式，或將它們指定為「系統進程」。

 Microsoft Windows 支援多個處理常式。 每個進程都可以有一或多個執行緒，而且每個執行緒都可以有一或多個相關聯的最上層視窗。 每個最上層視窗都可以擁有一系列的視窗。 + 符號展示層級已折迭。 折迭的視圖包含每個進程一行。 按一下 + 符號展開層級。

 如果您想要檢查特定的系統進程（通常會對應至執行中的程式），請使用 [進程]。 系統會以模組名稱來識別處理常式，或將它們指定為「系統進程」。 若要尋找處理常式，請折迭樹狀結構並搜尋清單。

## <a name="procedures"></a>程序

#### <a name="to-open-the-processes-view"></a>開啟進程視圖

1. 從 **Spy** 功能表中，選擇 [ **進程**]。

   ![Spy&#43;&#43; 進程視圖](../debugger/media/spy--_processes.png "Spy + + _Processes") Spy + + 進程視圖

   上圖顯示展開進程和執行緒節點的進程視圖。

### <a name="in-this-section"></a>本節內容
 [在進程中搜尋進程視圖](../debugger/how-to-search-for-a-process-in-processes-view.md) 說明如何在 [進程] view 中尋找特定的進程。

 [顯示進程屬性](../debugger/how-to-display-process-properties.md) 說明如何顯示訊息的詳細資訊。

### <a name="related-sections"></a>相關章節
 [Spy + + Views](../debugger/spy-increment-views.md) 說明 windows、訊息、進程和執行緒的 Spy + + 樹狀檢視。

 [使用 Spy + +](../debugger/using-spy-increment.md) 介紹 Spy + + 工具，並說明其使用方式。

 [進程搜尋對話方塊](../debugger/process-search-dialog-box.md) 用來尋找進程視圖中特定進程的節點。

 [進程屬性對話方塊](../debugger/process-properties-dialog-box.md) 顯示在 [進程] View 中選取之進程的屬性。

 [Spy + + 參考](../debugger/spy-increment-reference.md) 包含描述每個 Spy + + 功能表和對話方塊的章節。