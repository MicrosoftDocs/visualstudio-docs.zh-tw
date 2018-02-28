---
title: "在 Visual Studio 中產生方法覆寫 | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: df0eecdeb2aad15e1da68cef3b125c3c95f57e78
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="generate-an-override-in-visual-studio"></a>在 Visual Studio 中產生覆寫

此程式碼產生適用於：

- C#

- Visual Basic

**功能：**讓您針對任何可從基底類別覆寫的方法立即產生程式碼。

**時機：**您想要覆寫基底類別方法並自動產生簽章。

**原因：**您可以自行撰寫方法簽章，不過，此功能將可自動產生簽章。

## <a name="how-to"></a>操作說明

1. 在 C# 輸入 `override` 或在 Visual Basic 輸入 `Overrides`，後面接著一個空格，可在此處插入覆寫方法。

   - C#: 

    ![覆寫 IntelliSense C#](media/override-intellisense-cs.png)

   - Visual Basic：

    ![覆寫 IntelliSense VB](media/override-intellisense-vb.png)

1. 從基底類別選取您想要覆寫的方法。

   > [!TIP]
   > - 請使用屬性圖示 ![屬性圖示](media/override-property-cs.png) 來顯示或隱藏清單中的屬性。
   > - 請使用方法圖示 ![方法圖示](media/override-method-cs.png) 來顯示或隱藏清單中的方法。

   系統會把選取的方法或屬性新增至類別作為覆寫，並備妥以供實作。

   - C#: 

      ![覆寫結果 C#](media/override-result-cs.png)

   - Visual Basic：

      ![覆寫結果 VB](media/override-result-vb.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)
