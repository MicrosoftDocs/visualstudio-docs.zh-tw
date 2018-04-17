---
title: 來源檔案、 通用屬性、 方案屬性頁對話方塊偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aa83025b15fe3773220a2b27394890318d60c850
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>方案屬性頁對話方塊、通用屬性、偵錯原始程式檔
此屬性頁可指定對方案進行偵錯時，偵錯工具將於何處尋找原始程式檔。  
  
 若要存取**偵錯原始程式檔**屬性頁上，以滑鼠右鍵按一下方案中**方案總管 中**選取**屬性**從捷徑功能表。 展開**通用屬性**資料夾，然後按一下**偵錯原始程式檔**頁面。  
  
 **包含原始程式碼的目錄**  
 包含目錄清單，偵錯工具對方案進行偵錯時，會在這個清單中搜尋原始程式檔。 另外也會搜尋所指定目錄的子目錄。  
  
 **不要尋找這些原始程式檔**  
 輸入要讓偵錯工具讀取時排除的任何檔案名稱。 如果偵錯工具在上面其中一個指定的目錄中找到這些檔案中的某一個，就會忽略該檔案。 如果**尋找原始碼**時進行偵錯，而您按一下對話方塊中出現**取消**，您要搜尋的檔案會加入到此清單，如此偵錯工具將不會繼續搜尋該檔案。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)