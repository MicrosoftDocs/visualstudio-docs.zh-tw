---
title: 將 typeof 轉換成 nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 233393114883c2a9833aa7ec82f0d78f0ef33bae
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251280"
---
# <a name="convert-typeof-to-nameof"></a>將 `typeof` 轉換為 `nameof`

此重構適用於：

- C#
- Visual Basic

**功能：** 可讓您將 c # 中的實例轉換成，並將的 `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` 實例轉換 `GetType(<QualifiedType>).Name` 成 `NameOf(<QualifiedType>)` Visual Basic 中的。

時機 **：** 的所有實例 `typeof(<QualifiedType>).Name` 都 `someType` 不是泛型型別。 這是必要的排除動作，因為這種情況不會傳回與相同的字串值 `nameof(<QualifiedType>)` 。 Visual Basic 實例也是如此。

**原因：** 使用 `nameof` 而不是的名稱， `type` 可避免與抓取物件相關的反映 `type` ，而且是撰寫它的更實際方式。

## <a name="how-to"></a>操作方式

1. 將游標放在 `typeof(<QualifiedType>).Name` c # 的實例內或 `GetType(<QualifiedType>).Name` Visual Basic 中的。
2. 按**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取下列其中一個選項：

- C#
  <br>選取 [**將 ' typeof ' 轉換為 ' nameof '**] 
   ![ 將 typeof 轉換成 nameof](media/convert-type-of.PNG)

- Visual Basic
  <br>選取 [ **將 ' GetType ' 轉換成 ' NameOf '** ] ![ 將 typeof 轉換成 NameOf](media/convert-get-type.PNG)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
