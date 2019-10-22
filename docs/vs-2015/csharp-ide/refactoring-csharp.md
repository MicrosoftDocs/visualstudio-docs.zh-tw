---
title: 重構（C#） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667506"
---
# <a name="refactoring-c"></a>重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

重構是藉由變更程式碼的內部結構，而不需要變更程式碼的外部行為，而改善您的程式碼的程式。

 視覺C#效果會在 [**重構**] 功能表上提供下列重構命令：

- [擷取方法重構 (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [重新命名重構 (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [封裝欄位重構 (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [擷取介面重構 (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [移除參數重構 (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [重新排序參數重構 [C#]](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>多專案重構
 Visual Studio 針對相同方案中的專案支援多專案重構。 更正跨檔案參考的所有重構作業，會在相同語言的所有專案中更正這些參考。 這適用于任何專案對專案的參考。 例如，如果您有參考類別庫的主控台應用程式，則當您重新命名類別庫類型（使用 `Rename` 重構作業）時，主控台應用程式中的類別庫類型參考也會一併更新。

## <a name="changes-preview"></a>變更預覽
 許多重構作業可讓您在認可至這些變更之前，先檢查重構作業會對程式碼執行的所有參考變更。 針對這些重構作業，[**預覽參考變更**] 選項會出現在 [重構] 對話方塊中。 選取該選項並接受重構作業之後，[**預覽變更] 對話方塊**隨即出現。 請注意，[**預覽變更**] 對話方塊有兩個視圖。 底部視圖會顯示您的程式碼，其中包含重構作業所造成的所有參考更新。 在 [**預覽變更**] 對話方塊上按下 [**取消**] 將會停止重構作業，而且不會對您的程式碼進行任何變更。

## <a name="refactoring-warnings"></a>重構警告
 如果編譯器完全不了解您的程式，而且重構引擎可能無法更新所有適當的參考，就會顯示警告對話方塊。 這個警告對話方塊也可讓您在認可變更之前，先在 [**預覽變更**] 對話方塊中預覽程式碼。

> [!NOTE]
> 如果方法包含語法錯誤（IDE 會以紅色波浪底線表示），則重構引擎不會更新該方法中專案的任何參考。 下列範例說明此行為。

 根據預設，如果您在沒有預覽參考變更的情況下執行重構作業，而且在程式中偵測到編譯錯誤，則開發環境會顯示此警告對話方塊。

 如果您執行的重構作業已啟用**預覽參考變更**，而且在程式中偵測到編譯錯誤，則開發環境會在預覽變更的底部顯示下列警告訊息對話方塊，而不是顯示 [**重構警告**] 對話方塊：

 **您的專案或它的其中一個相依性目前並未建立。參考可能不會更新。**

 這個重構警告僅適用于提供 [**預覽參考變更**] 選項的重構作業。

## <a name="error-tolerant-refactoring-and-verification-results"></a>錯誤容錯重構和驗證結果
 重構的容錯能力。 換句話說，您可以在無法建立的專案中執行重構。 不過，在這些情況下，重構程式可能不會正確地更新不明確的參考。

 [**驗證結果**] 對話方塊可以在重構引擎偵測到編譯錯誤時通知您，或發現重構作業不小心造成程式碼參考系結至與原本所系結的內容不同的專案（重新系結問題）。

 若要開啟 [驗證結果] 功能，請在 [**工具**] 功能表上按一下 [**選項**]。 在 [**選項**] 對話方塊中，展開 [**文字編輯器**]， **C#** 然後展開 []。 按一下 [ **Advanced** ]，然後選取 [**驗證重構的結果**] 核取方塊。

 [**驗證結果**] 對話方塊會區分兩種重新系結問題的差異。

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>其定義不再是已重新命名符號的參考
 當參考不再參考已重新命名的符號時，就會發生這種重新系結問題。 例如，請參考下列程式碼：

```csharp
class Example
{
    private int a;
    public Example(int b)
    {
        a = b;
    }
}
```

 如果您使用重構來將 `a` 重新命名為 `b`，則會出現此對話方塊。 已重新命名之變數的參考 `a` 現在會系結至傳遞至此函式的參數，而不是系結至欄位。

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>其定義現在會成為重新命名符號的參考
 這種重新系結問題發生在先前未參考已重新命名符號的參考時，會參考重新命名的符號。 例如，請參考下列程式碼：

```csharp
class Example
{
    private static void Method(object a) { }
    private static void OtherMethod(int a) { }
    static void Main(string[] args)
    {
        Method(5);
    }
}
```

 如果您使用重構來將 `OtherMethod` 重新命名為 `Method`，則會出現此對話方塊。 @No__t_0 中的參考現在指的是可接受 `int` 參數的多載方法，而不是接受 `object` 參數的多載方法。

## <a name="see-also"></a>請參閱
 [使用 Visual Studio 開發環境C# ](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)來瞭解[如何：還原C#重構程式碼片段](../ide/how-to-restore-csharp-refactoring-snippets.md)