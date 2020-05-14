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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093875"
---
# <a name="wrap-indent-and-align-refactorings"></a>使重構換行、縮排及對齊

## <a name="wrap-and-align-call-chains"></a>換行和對齊呼叫鏈結

此重構適用於：

- C#

- Visual Basic

**內容：** 允許您包裝和對齊方法調用鏈。

**何時：** 您有一個長鏈，由一個語句中的多個方法調用組成。

**原因：** 根據使用者首選項包裝或縮進長清單，讀取長清單會更容易。

### <a name="how-to"></a>操作方式

1. 將您的游標放在任何呼叫鏈結中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [換行呼叫鏈結]**** 或 [換行並對齊呼叫鏈結]**** 來接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>將參數或引數換行、縮排或對齊

此重構適用於：

- C#

- Visual Basic

**內容：** 允許您換行、縮進和對齊參數或參數。

**何時：** 您有一個方法聲明或調用，它具有多個參數或參數。

**原因：** 讀取參數或參數的長清單時，根據使用者首選項包裝或縮進這些參數或參數會更容易。

### <a name="how-to"></a>操作方式

1. 將游標放在參數清單中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

   ![使參數換行、縮排及對齊](media/wrap-parameters.png)

3. 選擇 **"包裝每個參數**以接受重構"。

## <a name="wrap-binary-expressions"></a>包裝二進位運算式

此重構適用於：

- C#

- Visual Basic

**內容：** 允許您包裝二進位運算式。

**何時：** 您有一個二進位運算式。

**原因：** 讀取二進位運算式在包裝到使用者首選項時更容易。

### <a name="how-to"></a>操作方式

1. 將游標放在二進位運算式中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
3. 選擇 **"換行"運算式**以接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-binary-expression.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
