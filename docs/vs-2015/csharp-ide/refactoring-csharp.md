---
title: 重構 (C#) |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa8fbfd8837fb35617b79089fffd11ea3b8d2e93
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444536"
---
# <a name="refactoring-c"></a>重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

重構是之後已經變更的程式碼的內部結構但不變更程式碼外部行為，改善您的程式碼的程序。  
  
 Visual C# 上提供下列的重構命令**重構**功能表：  
  
- [擷取方法重構 (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
- [重新命名重構 (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
- [封裝欄位重構 (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
- [擷取介面重構 (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
- [移除參數重構 (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
- [重新排序參數重構 [C#]](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>多專案重構  
 Visual Studio 支援多專案重構為位於相同方案中的專案。 修正參考到檔案的重整作業的所有相同語言的所有專案更正這些參考。 這適用於任何專案對專案參考。 例如，如果您已參考類別庫中，當您重新命名類別庫類型的主控台應用程式 (使用`Rename`重構作業)，也會更新在主控台應用程式中的類別程式庫類型的參考。  
  
## <a name="changes-preview"></a>變更預覽  
 許多重構作業會提供一個機會，供您檢閱重構作業會在您的程式碼執行之前認可這些變更的所有參考變更。 重構作業，這些**過預覽參考變更**選項會出現在 [重構] 對話方塊中。 選取該選項，並接受重構作業之後,**預覽變更 對話方塊**會出現。 請注意，**預覽變更**對話方塊有兩個檢視。 下方檢視會顯示您的程式碼，因為重整作業的所有參考更新。 按下**取消**上**預覽變更**對話方塊將會停止重構作業，而且不會變更您的程式碼。  
  
## <a name="refactoring-warnings"></a>重構的警告  
 如果編譯器就不需要完整了解您的程式，您也可以重構引擎可能會不會更新所有適當的參考，則會顯示警告對話方塊。 這個警告對話方塊也會提供您在預覽中的程式碼的機會**預覽變更**認可變更之前的對話方塊。  
  
> [!NOTE]
> 如果方法包含語法錯誤 （表示 IDE 在有紅色波浪底線），然後重構引擎不會更新任何參考該方法中的項目。 下列範例說明此行為。  
  
 根據預設，如果您執行重構作業，而不需要預覽參考變更，並編譯錯誤偵測到您在程式中，然後在開發環境會顯示這個警告對話方塊。  
  
 如果您執行重構作業可**預覽參考變更**啟用和編譯錯誤偵測到在您的程式，則在開發環境會在底部顯示下列警告訊息**預覽變更**對話方塊中，代替顯示**警告重整** 對話方塊中：  
  
 **您的專案或其相依性的其中一個目前尚未建置。參考可能不會更新。**  
  
 這個重構的警告只適用於重構所提供的作業**預覽參考變更**選項。  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>容錯重整和驗證結果  
 重構是相容的錯誤。 換句話說，您可以執行無法建置的專案中重構作業。 不過，在這些情況下重構的程序可能無法正確更新模稜兩可的參考。  
  
 **驗證結果**重構引擎偵測到編譯錯誤，或探索重構作業會不小心造成程式碼參考繫結至不同的是什麼項目時，對話方塊可以通知您原本繫結 （重新繫結的問題）。  
  
 若要開啟驗證結果功能，請在**工具**功能表上，按一下**選項**。 在 **選項**對話方塊方塊中，展開**文字編輯器**，然後展開**C#**。 按一下 [**進階**，然後選取**驗證重構結果**] 核取方塊。  
  
 **驗證結果** 對話方塊會區分兩種類型的重新繫結問題之間的差異。  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>其定義將不再重新命名的符號的參考  
 參考不會再參考已重新命名符號時，就會發生這種重新繫結的問題。 例如，請參考下列程式碼：  
  
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
  
 如果您使用重構重新命名`a`至`b`，會出現此對話方塊。 重新命名的變數參考`a`現在繫結至傳遞給建構函式，而不是欄位的繫結的參數。  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>其定義現在將會成為已重新命名的符號的參考  
 當先前未參考已重新命名符號現在的參考會參考已重新命名符號時，就會發生這種重新繫結的問題。 例如，請參考下列程式碼：  
  
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
  
 如果您使用重構重新命名`OtherMethod`至`Method`，會出現此對話方塊。 中的參考`Main`現在指的是多載的方法，接受`int`而不是多載方法可接受的參數`object`參數。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Studio 開發環境適用於 C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [如何：還原 C# 重構程式碼片段](../ide/how-to-restore-csharp-refactoring-snippets.md)