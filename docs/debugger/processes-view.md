---
title: 處理序檢視 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b898713b456afd72f6453bad01028af9090b8dd2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922951"
---
# <a name="processes-view"></a>處理序檢視
處理序檢視會顯示您系統上的所有作用中處理序樹狀結構。 會顯示處理序識別碼和模組名稱。 如果您想要檢查特定的系統程序，通常對應於執行程式，請使用處理序檢視。 處理程序會以模組名稱識別，或指定 [系統處理序]。  
  
 Microsoft Windows 支援多個處理序。 每個處理序可以有一或多個執行緒，以及每個執行緒可以有一個或多個相關聯的最上層視窗。 每個最上層的視窗可以擁有一系列的視窗。 A （+ 符號） 表示層級會摺疊。 摺疊的檢視是由每個處理序的一列所組成。 按一下 + 符號展開的層級。  
  
 如果您想要檢查特定的系統程序，通常對應於執行程式，請使用處理序檢視。 處理程序會以模組名稱識別，或指定 [系統處理序]。 若要尋找處理程序，摺疊樹狀結構，並在清單中搜尋。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-open-the-processes-view"></a>若要開啟 處理序檢視  
  
1. 從**Spy**功能表上，選擇**處理序**。  
  
   ![Spy&#43; &#43;處理序檢視](../debugger/media/spy--_processes.png "Spy + + _Processes")  
   Spy++ 處理序檢視  
  
   上圖顯示處理序檢視處理序和執行緒展開的節點。  
  
### <a name="in-this-section"></a>本節內容  
 [搜尋處理序檢視中的處理序](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 說明如何在處理序檢視中找到特定的處理程序。  
  
 [顯示處理序屬性](../debugger/how-to-display-process-properties.md)  
 說明如何顯示一則訊息的詳細資訊。  
  
### <a name="related-sections"></a>相關章節  
 [Spy++ 檢視](../debugger/spy-increment-views.md)  
 說明 windows、 訊息、 處理程序和執行緒的 Spy + + 樹狀結構檢視。  
  
 [使用 Spy++](../debugger/using-spy-increment.md)  
 介紹 Spy + + 工具，並說明如何使用它。  
  
 [處理序搜尋對話方塊](../debugger/process-search-dialog-box.md)  
 用來尋找特定的處理程序，在處理序檢視中的節點。  
  
 [處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)  
 顯示處理程序在處理序檢視中選取屬性。  
  
 [Spy++ 參考](../debugger/spy-increment-reference.md)  
 包含描述每個 Spy + + 功能表和對話方塊方塊中的區段。