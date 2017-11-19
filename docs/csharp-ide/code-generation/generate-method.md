---
title: "產生的方法-產生程式碼 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 626db0d9c62fc606539fc9d72fc14c3651dca7ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-c"></a>在 C# 中產生方法 #
**項目：**可讓您立即將方法加入至類別。 

**當：**您引入新的方法，而且想要正確地自動宣告。  

**原因：**您無法宣告的方法和參數後才能使用它，不過這項功能會自動產生的宣告。 

**如何：**

1. 將游標放在該行其中會有紅色曲線，表示您已使用還不存在的方法。

   ![反白顯示的程式碼](media/method_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**產生方法**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**產生方法**從預覽視窗快顯視窗。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![產生方法預覽](media/method_preview.png)

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。

1. 方法會自動建立的任何參數，從其使用方式推斷。

   ![產生方法結果](media/method_result.png)

## <a name="see-also"></a>另請參閱  
[程式碼產生 (C#)](../code-generation-csharp.md)  
[預覽變更](../../ide/preview-changes.md)
