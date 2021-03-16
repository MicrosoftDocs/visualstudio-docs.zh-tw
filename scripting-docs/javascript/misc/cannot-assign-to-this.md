---
description: 您已嘗試將值指派給此值。
title: 無法指派給 ' this ' |Microsoft 檔
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c52118ee78b7ecb7efa94dd6d86cc4fb34c7d1f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571827"
---
# <a name="cannot-assign-to-this"></a>無法指派給 'this'
您已嘗試將值指派給 **此** 值。 **這** 是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 代表下列其中一個關鍵字的關鍵字：

- 目前正在執行方法的物件，

- 如果目前沒有方法 (，或方法不屬於任何其他物件) ，則為全域物件。

方法是透過物件叫用的函 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 式。 在方法中， **這個** 關鍵字是對物件的參考，方法是透過 (叫用類別的函式並使用 **new** 運算子) 所建立的物件。

在方法內，您可以使用 **這個** 來參考目前的物件，但是無法指派新的值給 **這個** 物件。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 請勿嘗試指派 **至此**。 若要存取具現化物件的屬性或方法，請使用點運算子 (例如， **circle. 半徑**) 。

  > [!NOTE]
  > 您無法將使用者建立 **的變數命名** 為：它是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 保留字。

## <a name="see-also"></a>另請參閱

- [這個語句](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/this)
- [指令碼疑難排解](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
