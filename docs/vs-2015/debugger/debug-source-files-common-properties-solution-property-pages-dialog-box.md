---
title: 偵錯來源檔案、 通用屬性、 方案屬性頁對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e2dcac4c105753febc86d3bec6e5dc0035e268
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253808"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>方案屬性頁對話方塊、通用屬性、偵錯原始程式檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此屬性頁可指定對方案進行偵錯時，偵錯工具將於何處尋找原始程式檔。  
  
 若要存取**偵錯原始程式檔**屬性頁上，以滑鼠右鍵按一下您的方案中**方案總管** ，然後選取**屬性**從捷徑功能表。 依序展開**通用屬性**資料夾，然後按一下**偵錯原始程式檔**頁面。  
  
 **包含原始程式碼的目錄**  
 包含目錄清單，偵錯工具對方案進行偵錯時，會在這個清單中搜尋原始程式檔。 另外也會搜尋所指定目錄的子目錄。  
  
 **不要尋找這些原始程式檔**  
 輸入要讓偵錯工具讀取時排除的任何檔案名稱。 如果偵錯工具在上面其中一個指定的目錄中找到這些檔案中的某一個，就會忽略該檔案。 如果**尋找來源**時進行偵錯，而您按一下對話方塊中出現**取消**，您要搜尋的檔案取得新增至此清單，讓偵錯工具將不會繼續搜尋該檔案。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)



