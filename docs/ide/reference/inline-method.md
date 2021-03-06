---
title: 內嵌方法
description: 瞭解如何使用 Visual Studio 中的 [快速動作與重構] 功能表來重構內嵌方法宣告，並提供更清楚的語法。
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 80313cf0dd9b828c9602fdf8ebff022342faa0fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852358"
---
# <a name="inline-method"></a>內嵌方法

此重構適用於：

- C#

- Visual Basic

事項 **：** 內嵌方法重構。 

時機 **：** 您想要以移除原始方法宣告的選項，取代單一語句主體內的靜態、實例和擴充方法的使用方式。

**原因：**  這種重構將提供更清楚的語法。

## <a name="how-to"></a>使用方法

1. 將插入號放在方法的使用方式上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取下列其中一個選項： 
    
   選取 [Inline `<QualifiedMethodName>`] \(內嵌 `<QualifiedMethodName>`\) 來移除內嵌方法的宣告：

    ![在 Visual Studio 中，[快速動作與重構] 功能表的 linkeddataformupdated 螢幕擷取畫面，其中已選取 [轉換 ' Inline ' CreateWidget (] # A1 '，並顯示 c # 程式碼變更。](media/inline-method-remove-declaration.png)

   選取 [Inline and keep `<QualifiedMethodName>`] \(內嵌並保留 `<QualifiedMethodName>`\) 來保留原方法的宣告：

    ![Visual Studio 中的 [快速動作與重構] 功能表的 linkeddataformupdated 螢幕擷取畫面，其中已選取 [內嵌] 和 [保留 ' CreateWidget ( # A1]，並顯示 c # 程式碼變更。](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
