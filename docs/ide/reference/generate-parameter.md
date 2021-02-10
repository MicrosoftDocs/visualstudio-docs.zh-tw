---
title: 產生參數重構
description: 瞭解如何使用 [快速動作與重構] 功能表來自動產生方法參數。
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 33e2be19e3a5a83d89e722aa0c1a1154c8196939
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968030"
---
# <a name="generate-parameter"></a>產生參數

此重構適用於：

- C#

- Visual Basic

事項 **：** 自動產生方法參數。

時機 **：** 您可以參考不存在於目前內容中的方法中的變數，並接收錯誤;您可以產生參數作為程式碼修正程式。 

**原因：** 您可以快速修改方法簽章，而不會遺失內容。

## <a name="how-to"></a>使用方法

1. 將游標放在變數名稱中，然後按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
1. 選取 [產生參數]。

   ![產生參數](media/generate-parameter.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
