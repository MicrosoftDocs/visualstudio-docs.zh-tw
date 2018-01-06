---
title: "導入的本機變數的程式碼產生 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9caafd73703478c75d7d91708ddcf5d14139e7fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>引進在 Visual Basic 中的本機變數
**項目：**可讓您立即產生一個本機變數來取代現有的運算式。

**當：**有無法輕易地重複用稍後就好像在本機變數中的程式碼。  

**原因：**您可以複製及貼上程式碼多次使用各種不同的位置，不過它會為執行一次的作業、 將結果儲存在本機變數中，並使用本機變數 throughought 更好。 

**如何：**

1. 反白顯示您想要指派給新的本機變數的運算式。

   ![反白顯示的程式碼](media/local_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**引進區域 （的所有項目） '*運算式*' * * 從預覽視窗快顯視窗，其中*運算式*是您所反白顯示的程式碼。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**引進區域 （的所有項目） '*運算式*' * * 預覽視窗快顯視窗中，從其中*運算式*是您所反白顯示的程式碼。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![導入本機預覽](media/local_preview.png)

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。

1. 本機變數會自動建立的型別從其使用方式推斷。  指定新的本機變數的新名稱來輸入。

   ![導入本機的結果](media/local_result.png)

   >[!NOTE]
   >您可以使用**..所有出現的...**取代找不到，所選的運算式不只是一個您有特別反白顯示的每個執行個體的功能表選項。

## <a name="see-also"></a>請參閱  
[程式碼產生 (Visual Basic)](../code-generation-vb.md)  
[預覽變更](../../ide/preview-changes.md) 