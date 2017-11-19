---
title: "如何： 使用中斷點與 XSLT |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c077cab7bf02023d0bfb1714940f98020600477
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-breakpoints-with-xslt"></a>HOW TO：搭配使用中斷點與 XSLT
您可在 XSLT 樣式表或 XML 來源文件中設定中斷點。 如果您在標記上設定了中斷點，則在開始執行時，中斷點會移至下一個具有原始程式行資訊的陳述式 (Statement)。  
  
 如需詳細資訊，請參閱[偵錯基本概念： 中斷點](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)。  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>在樣式表中設定中斷點  
 中斷點可在 XSLT 樣式表的開始標記、結束標記及文字節點上設定。 中斷點也可以在指令碼區塊的程式碼上設定。  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>在樣式表中設定中斷點  
  
1.  在 XML 編輯器中開啟樣式表。  
  
2.  將游標放在中斷點的位置，請以滑鼠右鍵按一下，指向**中斷點**，然後按一下**插入中斷點**。  
  
3.  按一下 [瀏覽按鈕 (**...**) 上**輸入**文件屬性] 視窗的欄位。  
  
4.  找出 XML 來源文件並按一下**開啟**。  
  
     這會設定用於 XSLT 轉換的來源文件檔案。  
  
5.  按一下**偵錯 XSL** XML 編輯器工具列上的按鈕。  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>在 XML 來源文件中設定中斷點  
 中斷點可以在 XML 來源文件的項目、屬性、命名空間節點、註解、處理指示與文字節點上設定。 您無法在文件節點或從父項目繼承的命名空間節點上設定中斷點。  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>在 XML 來源文件中設定中斷點  
  
1.  在 XML 編輯器中開啟 XML 文件。  
  
2.  將游標放在中斷點的位置，請以滑鼠右鍵按一下，指向**中斷點**，然後按一下**插入中斷點**。  
  
3.  按一下 [瀏覽按鈕 (**...**) 上**樣式表**文件屬性] 視窗的欄位。  
  
4.  找出 XML 來源文件並按一下**開啟**。  
  
     這會設定用於 XSLT 轉換的來源文件檔案。  
  
5.  按一下**偵錯 XSL** XML 編輯器工具列上的按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)