---
title: 將區域函式轉換為方法
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 55c82aa896de5c3f3bf18468a1da98253a3def74
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324673"
---
# <a name="convert-local-function-to-method"></a>將區域函式轉換為方法

此重構適用於：

- C#
- Visual Basic

**功能：** 將區域函式轉換為方法

**時機：** 您有要在目前本機內容以外定義的區域函式。

**原因：** 建議您將區域函式轉換為方法，以便您可以在本機內容之外呼叫。 當您的區域函式變得太長時，建議您轉換為方法。 在個別的方法中定義，可讓您的程式碼較容易閱讀。

## <a name="convert-local-function-to-method-refactoring"></a>將區域函式轉換為方法重構

1. 將游標放在區域函式中。

    ![將區域函式轉換為方法](media/convert-local-function-to-method.png)

2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

    ![將區域函式轉換為方法程式碼修正](media/convert-local-function-to-method-codefix.png)

2. 按 **Enter** 鍵接受重構。

    ![將區域函式轉換為方法結果](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的秘訣](../../ide/visual-studio-2017-for-dotnet-developers.md)
