---
title: 使重構換行、縮排及對齊
description: 了解如何換行和對齊方法呼叫的鏈結。
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093875"
---
# <a name="wrap-indent-and-align-refactorings"></a>使重構換行、縮排及對齊

## <a name="wrap-and-align-call-chains"></a>換行和對齊呼叫鏈結

此重構適用於：

- C#

- Visual Basic

事項 **：** 讓您包裝和對齊方法呼叫的鏈。

時機 **：** 在一個語句中，您有數個方法呼叫所組成的長鏈。

**原因：** 當您根據使用者喜好進行包裝或縮排時，讀取長清單會比較容易。

### <a name="how-to"></a>操作方式

1. 將您的游標放在任何呼叫鏈結中。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [換行呼叫鏈結]**** 或 [換行並對齊呼叫鏈結]**** 來接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>將參數或引數換行、縮排或對齊

此重構適用於：

- C#

- Visual Basic

事項 **：** 讓您將參數或引數換行、縮排及對齊。

時機 **：** 您有一個具有多個參數或引數的方法宣告或呼叫。

**原因：** 當您根據使用者喜好設定來進行包裝或縮排時，讀取較長的參數或引數清單會比較容易。

### <a name="how-to"></a>操作方式

1. 將游標放在參數清單中。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

   ![使參數換行、縮排及對齊](media/wrap-parameters.png)

3. 選取 [將 **每個參數換行** ] 以接受重構。

## <a name="wrap-binary-expressions"></a>包裝二進位運算式

此重構適用於：

- C#

- Visual Basic

事項 **：** 可讓您包裝二進位運算式。

時機 **：** 您有一個二元運算式。

**原因：** 將二進位運算式包裝到使用者喜好設定時，讀取二進位運算式會比較容易。

### <a name="how-to"></a>操作方式

1. 將游標放在二元運算式中。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [ **換行運算式** ] 以接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-binary-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
