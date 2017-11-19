---
title: "產生的覆寫-產生程式碼 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d2972cfe2ea4481ab8f5eab6284277615d1d64a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-c"></a>在 C# 中產生的覆寫 #
**項目：**可讓您立即產生，您可以覆寫任何方法的程式碼基底類別。 

**當：**您想要覆寫基底類別方法，並自動產生的簽章。  

**原因：**您無法將方法簽章自行撰寫，不過這項功能將會自動產生的簽章。 

**如何：**

1. 型別**覆寫**關鍵字，後面接著一個空格，其中您想要插入的覆寫的方法簽章和 IntelliSense 下拉式清單會出現。

   ![覆寫 IntelliSense](media/override_intellisense.png)

1. 選取您想要覆寫基底類別，按一下使用滑鼠或按鍵盤與瀏覽至它的方法**Enter**。

   >[!TIP]
   >* 使用 [屬性] 圖示 ![屬性圖示](media/override_property.png) 若要顯示或隱藏的屬性清單中。
   >* 使用方法圖示 ![屬性圖示](media/override_method.png) 若要顯示或隱藏在清單中的方法。

1. 選取的方法或屬性將會加入至類別是覆寫，準備好要實作。

   ![覆寫結果](media/override_result.png)

## <a name="see-also"></a>另請參閱  
[程式碼產生 (C#)](../code-generation-csharp.md)  
