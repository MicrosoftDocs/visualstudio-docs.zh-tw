---
title: 內嵌方法
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402243"
---
# <a name="inline-method"></a>內嵌方法

此重構適用於：

- C#

- Visual Basic

事項 **：** 內嵌方法重構。 

時機 **：** 您想要以移除原始方法宣告的選項，取代單一語句主體內的靜態、實例和擴充方法的使用方式。

**原因：**  這種重構將提供更清楚的語法。

## <a name="how-to"></a>操作方式

1. 將插入號放在方法的使用方式上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取下列其中一個選項： 
    
   選取 [Inline `<QualifiedMethodName>`] \(內嵌 `<QualifiedMethodName>`\) 來移除內嵌方法的宣告：

    ![將類別設為抽象](media/inline-method-remove-declaration.png)

   選取 [Inline and keep `<QualifiedMethodName>`] \(內嵌並保留 `<QualifiedMethodName>`\) 來保留原方法的宣告：

    ![將類別設為抽象](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>請參閱

- [重構](../refactoring-in-visual-studio.md)
