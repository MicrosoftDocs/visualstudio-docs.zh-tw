---
title: 產生參數重構
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329088"
---
# <a name="generate-parameter"></a>產生參數

此重構適用於：

- C#

**功能：** 自動產生方法帳戶。

**時機：** 目前的內容中沒有所參考方法中的變數，並收到錯誤；您可以產生參數做為程式碼修正。 

**原因：** 您可以在不會遺失內容的情況下，快速修改方法簽章。

## <a name="how-to"></a>操作說明

1. 將您的游標放在變數名稱中並按下 **Ctrl**+ **。** 以觸發 [快速動作與重構]  功能表。
1. 選取 [產生參數]  。

   ![產生參數](media/generate-parameter.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
