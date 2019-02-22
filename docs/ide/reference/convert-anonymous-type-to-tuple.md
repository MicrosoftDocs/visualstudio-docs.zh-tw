---
title: 將匿名型別轉換為元組
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335779"
---
# <a name="convert-anonymous-type-to-tuple"></a>將匿名型別轉換為元組

此重構適用於：

- C#

**功能：** 將匿名型別轉換為元組。

**時機：** 您有適合作為元組的匿名型別。

**原因：**[元組](/dotnet/csharp/tuples)有助於讓語法保持精簡。 這個快速動作讓這項 C# 功能運用上更加輕鬆。

## <a name="how-to"></a>操作說明

1. 將游標放在匿名型別中。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![將匿名型別轉換為元組](media/convert-anon-to-tuple.png)

2. 按 **Enter** 鍵接受重構。

   ![將匿名型別轉換為元組](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
