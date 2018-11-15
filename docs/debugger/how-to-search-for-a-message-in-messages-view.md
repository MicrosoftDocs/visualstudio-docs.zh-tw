---
title: 如何： 在訊息檢視中的訊息搜尋 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9c00eea2034651298ff62bc50741971fc0369a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844909"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>如何：在訊息檢視中搜尋訊息
您可以使用其控制代碼、 類型或訊息識別碼，做為搜尋準則來搜尋特定訊息在訊息檢視中。 其中任何一個，或組合，會是有效的搜尋準則。 也可以指定搜尋的初始方向。 在對話方塊中的欄位會預先載入的目前選取的訊息屬性。  
  
### <a name="to-search-for-a-message-in-messages-view"></a>若要搜尋在訊息檢視中的訊息  
  
1. 因此排列的視窗，Spy + + 和作用[訊息檢視](../debugger/messages-view.md)視窗會顯示。  
  
2. 從**搜尋**功能表上，選擇**尋找訊息**。  
  
    [訊息搜尋對話方塊](../debugger/message-search-dialog-box.md)隨即開啟。  
  
3. 拖曳**搜尋工具**移轉所需的視窗。 當您拖曳工具，**訊息搜尋** 對話方塊上選取的視窗會顯示詳細資料。  
  
   - 或 -  
  
     如果您有您想要檢查其訊息的視窗控制代碼，將它輸入**處理**文字方塊。  
  
   - 或 -  
  
     如果您知道訊息類型和/或您想要的訊息識別碼，請選取 從**型別**並**訊息**下拉式功能表，並清除**處理**文字方塊。  
  
4. 清除，您不想指定值的任何欄位。  
  
   > [!TIP]
   >  若要減少螢幕混亂的情形，請選取**隱藏 spy + +** 選項。 此選項會隱藏主 Spy + + 視窗中，並且只留下**尋找視窗**對話方塊顯示在其他應用程式之上。 當您按一下 還原 Spy + + 主要視窗**確定**或是**取消**，或清除**隱藏 Spy + +** 選項。  
  
5. 選擇**向上**或是**向下**初始搜尋的方向。  
  
6. 按一下 [確定 **Deploying Office Solutions**]。  
  
   如果找到相符的訊息時，它會反白顯示在訊息的 [檢視] 視窗。 請參閱[訊息檢視](../debugger/messages-view.md)。