---
title: 產生方法覆寫
description: 瞭解如何立即產生可從基類覆寫之任何方法的程式碼。
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f27adacc39c53bf46b3a2ee09c71ae27b47f928
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617483"
---
# <a name="generate-an-override-in-visual-studio"></a>在 Visual Studio 中產生覆寫

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 讓您針對任何可從基底類別覆寫的方法立即產生程式碼。

**時機：** 您想要覆寫基底類別方法並自動產生簽章。

**原因：** 您可以自行撰寫方法簽章，不過，此功能將可自動產生簽章。

## <a name="how-to"></a>操作方式

1. 在 C# 輸入 `override` 或在 Visual Basic 輸入 `Overrides`，後面接著一個空格，可在此處插入覆寫方法。

   - C#：

      ![覆寫 IntelliSense C#](media/override-intellisense-cs.png)

   - Visual Basic：

      ![覆寫 IntelliSense VB](media/override-intellisense-vb.png)

2. 從基底類別選取您想要覆寫的方法。

   > [!TIP]
   > - 請使用屬性圖示 ![屬性圖示](media/override-property-cs.png) 來顯示或隱藏清單中的屬性。
   > - 請使用方法圖示 ![方法圖示](media/override-method-cs.png) 來顯示或隱藏清單中的方法。

   系統會把選取的方法或屬性新增至類別作為覆寫，並備妥以供實作。

   - C#：

       ![覆寫結果 C#](media/override-result-cs.png)

   - Visual Basic：

       ![覆寫結果 VB](media/override-result-vb.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
