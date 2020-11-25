---
title: 將 Get 方法轉換成屬性或從屬性轉換
description: 瞭解如何使用 [快速動作] 和 [重構] 功能表，將 Get 方法 (，以及選擇性地將 Set 方法) 轉換為屬性。
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3aa7831c56068c826c9bbecf97d7115331243251
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039819"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>將 Get 方法轉換為屬性 / 將屬性轉換為 Get 方法的重構

這些重構適用於：

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>將 Get 方法轉換為屬性

**功能：** 讓您將 Get 方法轉換為屬性 (以及視需要轉換 Set 方法)。

**時機：** 您有未包含任何邏輯的 Get 方法。

### <a name="how-to"></a>操作方式

1. 將游標放在 Get 方法名稱中。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以屬性取代方法]。
   - **滑鼠**
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以屬性取代方法]。

1. (選擇性) 如果您有 Set 方法，您也可以在此時選取 [以屬性取代 Get 方法和 Set 方法] 來轉換 Set 方法。

1. 如果您滿意程式碼預覽中的變更，請按 **Enter** 或從功能表中按一下修正，便會認可變更。

範例：

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>將屬性轉換為 Get 方法

**功能：** 讓您將屬性轉換為 Get 方法

**時機：** 您有不只是涉及立即設定和取得值的屬性

### <a name="how-to"></a>操作方式

1. 將游標放在 Get 方法名稱中。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以方法取代屬性]。
   - **滑鼠**
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以方法取代屬性]。

1. 如果您滿意程式碼預覽中的變更，請按 **Enter** 或從功能表中按一下修正，便會認可變更。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
