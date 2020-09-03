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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "71301685"
---
# <a name="convert-a-local-function-to-a-method"></a>將區域函式轉換為方法

此重構適用於：

- C#

事項 **：** 將區域函式轉換為方法。

時機 **：** 您有想要在目前本機內容以外定義的區域函式。

**原因：** 您想要將區域函式轉換為方法，讓您可以在本機內容之外呼叫。 當您的區域函式變得太長時，建議您轉換為方法。 在不同的方法中定義函式時，您的程式碼會更方便閱讀。

## <a name="convert-local-function-to-method-refactoring"></a>將區域函式轉換為方法重構

1. 將游標放在區域函式中。

    ![將區域函式轉換為方法程式碼範例](media/convert-local-function-to-method.png)

2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

    ![將區域函式轉換為方法程式碼修正範例](media/convert-local-function-to-method-codefix.png)

2. 按 Enter 以接受重構。

    ![將區域函式轉換為方法結果範例](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
