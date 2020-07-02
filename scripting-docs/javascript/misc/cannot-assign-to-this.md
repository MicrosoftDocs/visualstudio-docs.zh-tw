---
title: 無法指派給 ' this ' |Microsoft Docs
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
ms.openlocfilehash: f5c52153da64ff477d89b09d4af17169da18e4e1
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817316"
---
# <a name="cannot-assign-to-this"></a>無法指派給 'this'
您嘗試將值指派給**這個**。 **這**是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 參考下列任一項的關鍵字：

- 目前執行方法的物件。

- 如果沒有目前的方法（或方法不屬於任何其他物件），則為全域物件。

方法是透過物件叫用的函 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 式。 在方法內， **this**關鍵字是對叫用方法之物件的參考（這剛好是藉由使用**new**運算子叫用類別的函式所建立的物件）。

在方法內，您可以使用**這個**來參考目前的物件，但是您無法指派新的值給**這個**。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 請勿嘗試指派**至此**。 若要存取具現化物件的屬性或方法，請使用點運算子（例如**circle. radius**）。

  > [!NOTE]
  > 您不能將使用者建立**的變數命名**為。這是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 保留字。

## <a name="see-also"></a>另請參閱

- [此語句](../../javascript/reference/this-statement-javascript.md)
- [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)