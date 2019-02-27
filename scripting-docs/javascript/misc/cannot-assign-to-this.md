---
title: 無法指派給 'this' |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
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
ms.openlocfilehash: f147e591969f803533bb23ff16d73ee9af2c3d27
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839785"
---
# <a name="cannot-assign-to-this"></a>無法指派給 'this'
您嘗試指派值給**這**。 **這**是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]指的關鍵字：

- 目前執行方法，該物件

- 如果沒有目前的方法 （或任何其他物件到不屬於此方法） 則為全域物件。

方法是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]會透過物件叫用的函式。 在方法中，**這**關鍵字是透過叫用方法的物件的參考 (剛好是藉由叫用具有類別建構函式所建立的物件**新**運算子)。

在方法中，您可以使用**這**來參考目前的物件，但您無法指派新值給**這**。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 請勿嘗試將指派給**這**。 若要存取的屬性或方法具現化物件，使用點運算子 (例如**circle.radius**)。

  > [!NOTE]
  > 您不能命名為使用者建立的變數**這**; 它是[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]保留字。

## <a name="see-also"></a>另請參閱

- [this 陳述式](../../javascript/reference/this-statement-javascript.md)
- [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)