---
title: 如何：在 Windows View 中搜尋視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840252"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>如何：在視窗檢視中搜尋視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用其控制碼、標題、類別或其標題和類別的組合作為搜尋準則，在 Windows view 中搜尋特定視窗。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會在視窗樹狀結構中顯示所選視窗的屬性。  
  
 從展開至第二個層級的樹狀結構開始 (所有是桌面的子系) 的視窗，如此您就可以依類別名稱和標題來識別桌面層級視窗。 選擇桌面層級視窗之後，您可以展開該層級以尋找特定的子視窗。  
  
### <a name="to-search-for-a-window-in-windows-view"></a>在 Windows view 中搜尋視窗  
  
1. 因此排列的視窗，Spy + + [Windows 檢視](../debugger/windows-view.md) 視窗和 [目標] 視窗會顯示。  
  
2. 在 [ **搜尋** ] 功能表中，選擇 [ **尋找視窗]**。  
  
     [ [視窗搜尋] 對話方塊](../debugger/window-search-dialog-box.md) 隨即開啟。  
  
    > [!TIP]
    > 若要減少螢幕混亂，請選取 [ **隱藏 Spy** ] 選項。 此選項會隱藏主要的 Spy + + 視窗，而且只會在其他應用程式頂端顯示 [ **視窗搜尋** ] 對話方塊。 當您按一下 **[確定] 或 [** **取消**]，或清除 [ **隱藏 spy + +** ] 選項時，就會還原 Spy + + 主視窗。  
  
3. 將 [ **Finder] 工具** 拖曳至目標視窗。 當您拖曳工具時，[ **視窗搜尋** ] 對話方塊會顯示所選視窗的詳細資料。  
  
     -或-  
  
     如果您知道想要的視窗控制碼 (例如，從偵錯工具) ，您可以在 [ **控制碼** ] 方塊中輸入它。  
  
     -或-  
  
     如果您知道所需視窗的標題和/或類別，您可以在 [ **標題** ] 和 [ **類別** ] 文字方塊中輸入，然後清除 [ **控制碼** ] 文字方塊。  
  
4. 選擇 [ **向上** ] 或 [ **向下** ] 以取得搜尋的初始方向。  
  
5. 按一下 [確定]。  
  
     如果找到相符的視窗，它會在 [ [Windows View](../debugger/windows-view.md) ] 視窗中反白顯示。
