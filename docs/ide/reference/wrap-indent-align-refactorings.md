---
title: 換行、縮排及對齊重構
description: 了解如何換行和對齊方法呼叫的鏈結。
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527665"
---
# <a name="wrap-indent-and-align-refactorings"></a>換行、縮排及對齊重構

## <a name="wrap-and-align-call-chains"></a>換行並對齊呼叫鏈結

此重構適用於：

- C#

**功能：** 可讓您包裝和對齊方法呼叫的鏈。

時機 **：** 您有一個長鏈，其中包含一個語句中的數個方法呼叫。

**原因：** 當您根據使用者喜好設定來包裝或縮排時，讀取長清單會比較容易。

### <a name="how-to"></a>操作方式

1. 將您的游標放在任何呼叫鏈結中。
2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。
3. 選取 [換行呼叫鏈結] 或 [換行並對齊呼叫鏈結] 來接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>將參數或引數換行、縮排或對齊

此重構適用於：

- C#

- Visual Basic

**功能：** 可讓您換行、縮排及對齊參數或引數。

時機 **：** 您的方法宣告或呼叫具有多個參數或引數。

**原因：** 當您根據使用者喜好設定來包裝或縮排較長的參數或引數清單時，將會更容易閱讀。

### <a name="how-to"></a>操作方式

1. 將游標放在參數清單中。
2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。

   ![使參數換行、縮排及對齊](media/wrap-parameters.png)

3. 選取 [**換行每個參數**] 以接受重構。

## <a name="wrap-binary-expressions"></a>包裝二進位運算式

此重構適用於：

- C#

**功能：** 可讓您包裝二進位運算式。

時機 **：** 您有一個二元運算式。

**原因：** 當二進位運算式包裝為使用者喜好設定時，讀取它會比較容易。

### <a name="how-to"></a>操作方式

1. 將游標放在二進位運算式中。
2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。
3. 選取 [**換行運算式**] 以接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-binary-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
