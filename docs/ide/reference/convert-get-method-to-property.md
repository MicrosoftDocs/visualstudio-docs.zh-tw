---
title: 將 Get 方法轉換為屬性及將屬性轉換為 Get 方法
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bd3e534aec6ca1a8bbebfb5e1437d13e97d36e70
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990949"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>將 Get 方法轉換為屬性 / 將屬性轉換為 Get 方法的重構

這些重構適用於：

- C#

## <a name="convert-get-method-to-property"></a>將 Get 方法轉換為屬性

**功能：** 讓您將 Get 方法轉換為屬性 (以及視需要轉換 Set 方法)。

**時機：** 您有未包含任何邏輯的 Get 方法。

### <a name="how-to"></a>操作說明

1. 將游標放在 Get 方法名稱中。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以屬性取代方法]。
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

### <a name="how-to"></a>操作說明

1. 將游標放在 Get 方法名稱中。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以方法取代屬性]。
   - **滑鼠**
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [以方法取代屬性]。

1. 如果您滿意程式碼預覽中的變更，請按 **Enter** 或從功能表中按一下修正，便會認可變更。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)