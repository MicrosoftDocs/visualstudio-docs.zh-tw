---
title: 將區域函式轉換為方法
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a580077528c87e62f81e840ed6dee76ff1eac57f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968267"
---
# <a name="convert-a-local-function-to-a-method"></a>將區域函式轉換為方法

此重構適用於：

- C#
- Visual Basic

**功能：** 將區域函式轉換為方法。

**時機：** 您有要在目前本機內容以外定義的區域函式。

**原因：** 建議您將區域函式轉換為方法，以便您可以在本機內容之外呼叫。 當您的區域函式變得太長時，建議您轉換為方法。 在不同的方法中定義函式時，您的程式碼會更方便閱讀。

## <a name="convert-local-function-to-method-refactoring"></a>將區域函式轉換為方法重構

1. 將游標放在區域函式中。

    ![將區域函式轉換為方法程式碼範例](media/convert-local-function-to-method.png)

2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

    ![將區域函式轉換為方法程式碼修正範例](media/convert-local-function-to-method-codefix.png)

2. 按 Enter 以接受重構。

    ![將區域函式轉換為方法結果範例](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../../ide/visual-studio-2017-for-dotnet-developers.md)
