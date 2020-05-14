---
title: 將區域函式轉換為方法
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "71301685"
---
# <a name="convert-a-local-function-to-a-method"></a>將區域函式轉換為方法

此重構適用於：

- C#

**內容：** 將局部函數轉換為方法。

**何時：** 您有一個要在當前本地上下文之外定義的本地函數。

**原因：** 您希望將本地函數轉換為方法，以便可以在本地上下文之外調用它。 當您的區域函式變得太長時，建議您轉換為方法。 在不同的方法中定義函式時，您的程式碼會更方便閱讀。

## <a name="convert-local-function-to-method-refactoring"></a>將區域函式轉換為方法重構

1. 將游標放在區域函式中。

    ![將區域函式轉換為方法程式碼範例](media/convert-local-function-to-method.png)

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

    ![將區域函式轉換為方法程式碼修正範例](media/convert-local-function-to-method-codefix.png)

2. 按 Enter 以接受重構。

    ![將區域函式轉換為方法結果範例](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
