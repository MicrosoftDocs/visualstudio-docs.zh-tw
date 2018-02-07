---
title: "產生覆寫 - 程式碼產生 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-visual-basic"></a>使用 Visual Basic 來產生覆寫
**功能：**讓您針對任何可從基底類別覆寫的方法立即產生程式碼。 

**時機：**您想要覆寫基底類別方法並自動產生簽章。  

**原因：**您可以自行撰寫方法簽章，不過，此功能將可自動產生簽章。 

**做法：**

1. 在您想要插入被覆寫之方法簽章的位置輸入 **Overrides** 關鍵字，後面接著空格，系統將會顯示 IntelliSense 下拉式清單。

   ![覆寫 IntelliSense](media/override-intellisense-vb.png)

1. 從基底類別中，在您想要覆寫的方法上按一下滑鼠按鍵，或使用鍵盤來瀏覽至該方法並按 **Enter**，來選取該方法。

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. 系統將會把選取的方法或屬性新增至類別作為覆寫，並備妥以供實作。

   ![「覆寫」結果](media/override-result-vb.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md) 