---
title: 產生參數重構
description: 瞭解如何使用 [快速動作與重構] 功能表來自動產生方法參數。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 21e209f5be9072390df58e78db34811f886fa9c5
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617145"
---
# <a name="generate-parameter"></a>產生參數

此重構適用於：

- C#

- Visual Basic

事項 **：** 自動產生方法參數。

時機 **：** 您可以參考不存在於目前內容中的方法中的變數，並接收錯誤;您可以產生參數作為程式碼修正程式。 

**原因：** 您可以快速修改方法簽章，而不會遺失內容。

## <a name="how-to"></a>操作方式

1. 將游標放在變數名稱中，然後按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
1. 選取 [產生參數]。

   ![產生參數](media/generate-parameter.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
