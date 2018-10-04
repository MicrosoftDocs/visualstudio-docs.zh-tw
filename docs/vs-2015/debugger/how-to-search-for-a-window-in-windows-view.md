---
title: 如何： 搜尋在 [Windows] 檢視視窗 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 043e3e92004eb5b0995bc285e90a138f4dc902f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492026"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>如何：在視窗檢視中搜尋視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 搜尋視窗中檢視 Windows](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-window-in-windows-view)。  
  
您可以使用其控制代碼、 標題、 類別或其標題和類別的組合做為搜尋準則，搜尋 Windows 檢視在特定時間範圍。 您也可以指定搜尋的初始方向。 在對話方塊中的欄位會顯示在視窗樹狀目錄中的選取視窗的屬性。  
  
 開始使用第二個層級 (所有 windows 桌面的子系)，展開樹狀結構，讓您可以識別層級的桌面視窗中，其類別名稱和標題。 一旦您已選擇桌面層級的視窗，您可以展開該層次，以尋找特定的子視窗。  
  
### <a name="to-search-for-a-window-in-windows-view"></a>若要搜尋 [Windows] 檢視中的視窗  
  
1.  因此排列的視窗，Spy + + [Windows 檢視](../debugger/windows-view.md) 視窗和 [目標] 視窗會顯示。  
  
2.  從**搜尋**功能表上，選擇**尋找視窗**。  
  
     [視窗搜尋對話方塊](../debugger/window-search-dialog-box.md)隨即開啟。  
  
    > [!TIP]
    >  若要減少螢幕混亂的情形，請選取**隱藏 spy + +** 選項。 此選項會隱藏主 Spy + + 視窗，只留下**視窗中搜尋**對話方塊顯示在其他應用程式之上。 當您按一下 還原 Spy + + 主要視窗**確定**或是**取消**，或清除**隱藏 Spy + +** 選項。  
  
3.  拖曳**搜尋工具**目標範圍內。 當您拖曳工具，**視窗中搜尋** 對話方塊上選取的視窗會顯示詳細資料。  
  
     -或-  
  
     如果您知道您想要的視窗控制代碼 （例如，從 [偵錯工具） 時，可以在您輸入時**處理**] 方塊中。  
  
     -或-  
  
     如果您知道的標題和/或您想要的視窗類別，您可以輸入**標題**並**類別**文字方塊中，並清除**處理**文字方塊。  
  
4.  選擇**向上**或是**向下**初始搜尋的方向。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     如果找到相符的視窗，它會以醒目提示[Windows 檢視](../debugger/windows-view.md)視窗。



