---
title: 如何： 在視窗檢視中的視窗搜尋 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4333a79e76358216ce87697975dcb54173570534
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>如何：在視窗檢視中搜尋視窗
您可以使用其控制代碼、 標題、 類別或其標題和類別的組合做為搜尋準則，以搜尋特定的視窗，在視窗檢視中。 您也可以指定搜尋的初始方向。 在對話方塊中的欄位會顯示選取的視窗的屬性視窗樹狀目錄中。  
  
 開始與第二個層級 (所有 windows 桌面的子系)，展開樹狀目錄，讓您可以識別層級的桌面視窗中，其類別名稱，標題。 一旦您已選擇桌面層級的視窗，您可以展開層級來尋找特定的子視窗。  
  
### <a name="to-search-for-a-window-in-windows-view"></a>若要搜尋在視窗檢視中的視窗  
  
1.  排列的視窗，因此該 Spy + +，[視窗檢視](../debugger/windows-view.md) 視窗和 [目標] 視窗會顯示。  
  
2.  從**搜尋**功能表上，選擇**尋找視窗**。  
  
     [視窗搜尋對話方塊](../debugger/window-search-dialog-box.md)隨即開啟。  
  
    > [!TIP]
    >  若要減少螢幕混亂的情形，請選取**隱藏 spy + +** 選項。 這個選項對隱藏主 Spy + + 視窗，只留下**視窗搜尋**對話方塊在其他應用程式的上層。 當您按一下 還原 Spy + + 主視窗**確定**或**取消**，或當您清除**隱藏 Spy + +** 選項。  
  
3.  拖曳**搜尋工具**目標視窗之上。 當您拖曳工具，**視窗搜尋** 對話方塊上選取的視窗中顯示詳細資料。  
  
     - 或 -  
  
     如果您知道您想要的視窗控制代碼 （例如，從 偵錯工具） 時，您可以輸入在**處理**方塊。  
  
     - 或 -  
  
     如果您知道標題和/或您想要的視窗的類別，您可以輸入在**標題**和**類別**文字方塊中，然後清除**處理**文字方塊。  
  
4.  選擇**向上**或**向**搜尋初始方向。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     如果找到符合的視窗，它會反白顯示在[視窗檢視](../debugger/windows-view.md)視窗。