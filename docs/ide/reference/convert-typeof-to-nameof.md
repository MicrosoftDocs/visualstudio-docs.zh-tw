---
title: 將 typeof 轉換為 nameof
description: '瞭解如何使用 Visual Studio 中的 [快速動作與重構] 功能表，以 c # 和 GetType 中的 nameof 將 typeof 轉換成 NameOf 的 Visual Basic。'
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919697"
---
# <a name="convert-typeof-to-nameof"></a>將 `typeof` 轉換為 `nameof`

此重構適用於：

- C#
- Visual Basic

事項 **：** 可讓您在 c # 中將的實例轉換成， `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` 並 `GetType(<QualifiedType>).Name` `NameOf(<QualifiedType>)` 在 Visual Basic 中將的實例轉換為。

時機 **：** Where 的所有實例都 `typeof(<QualifiedType>).Name` `someType` 不是泛型型別。 這項排除是必要的，因為此案例不會傳回與相同的字串值 `nameof(<QualifiedType>)` 。 Visual Basic 實例也是如此。

**原因：** 使用 `nameof` 而不是的名稱 `type` 可避免與抓取物件相關的反映 `type` ，而且是撰寫它的更實際方式。

## <a name="how-to"></a>使用方法

1. 將游標放在 `typeof(<QualifiedType>).Name` c # 或 Visual Basic 中的實例內 `GetType(<QualifiedType>).Name` 。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取下列其中一個選項：

    - C#
      <br>Select **將 ' typeof ' 轉換成 ' nameof '**： ![ Visual Studio 中的 [快速動作與重構] 功能表的螢幕擷取畫面，其中已選取 [將 ' typeof ' 轉換成 ' nameof ']，並顯示 c # 程式碼變更。](media/convert-type-of.PNG)

    - Visual Basic
      <br>選取 [ **將 ' gettype ' 轉換成 ' NameOf '**： ![ Visual Studio 中的 [快速動作與重構] 功能表的螢幕擷取畫面，其中已選取 [將 ' gettype ' 轉換為 ' NameOf ']，並顯示 Visual Basic 程式碼變更。](media/convert-get-type.PNG)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
