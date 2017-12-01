---
title: "Get 方法轉換成屬性-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.openlocfilehash: d034b8835caf0a5e56a9ef32599cf9197f1e3e16
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Get 方法轉換成屬性/屬性轉換 Get 方法
## <a name="convert-get-method-to-property"></a>Get 方法轉換成屬性
**項目：**可讓您將 Get 方法轉換成屬性 （並選擇性地設定方法），反之亦然。

**當：**有 Get 的方法不包含任何邏輯。

**如何：**

1. 將游標放在您取得方法的名稱。

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**方法取代為屬性**從預覽視窗快顯視窗。 如果您有 Set 方法，所以您也可以轉換在此階段的 Set 方法藉由選取**取代 Get 方法和屬性的 Set 方法**。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**方法取代為屬性**從預覽視窗快顯視窗。 如果您有 Set 方法，所以您也可以轉換在此階段的 Set 方法藉由選取**取代 Get 方法和屬性的 Set 方法**。

1. 如果您滿意預覽程式碼中的變更，請按**Enter**或按一下 從功能表的修正，會認可變更。

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

## <a name="convert-property-to-get-method"></a>將屬性轉換成 Get 方法
**項目：**可讓您將屬性轉換成 Get 方法

**當：**牽涉到多個立即設定和取得值的屬性 

**如何：**

1. 將游標放在您取得方法的名稱。

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**屬性取代方法**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**屬性取代方法**從預覽視窗快顯視窗。

1. 如果您滿意預覽程式碼中的變更，請按**Enter**或按一下 從功能表的修正，會認可變更。

## <a name="see-also"></a>另請參閱  
[重構 (C#)](../refactoring-csharp.md)  
[預覽變更](../../ide/preview-changes.md)