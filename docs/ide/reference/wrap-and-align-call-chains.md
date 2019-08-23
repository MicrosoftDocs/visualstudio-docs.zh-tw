---
title: 換行和對齊呼叫鏈結
description: 了解如何換行和對齊方法呼叫的鏈結。
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620010"
---
# <a name="wrap-and-align-call-chains"></a>換行和對齊呼叫鏈結

此重構適用於：

- C#

**功能：** 讓您換行和對齊方法呼叫的鏈結。

**時機：** 您有由單一陳述式中數個方法呼叫組成的長鏈結。

**原因：** 當一長串清單依照使用者想要的方式換行或縮排後會讓閱讀更加輕鬆。

## <a name="how-to"></a>操作說明

1. 將您的游標放在任何呼叫鏈結中。
2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構]  功能表。
3. 選取 [換行呼叫鏈結]  或 [換行並對齊呼叫鏈結]  來接受重構。

   ![換行並對齊呼叫鏈結](media/wrap-call-chain.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
