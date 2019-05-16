---
title: 如何：將類別分割成部分類別 (類別設計工具) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 23d344d2f350b5b7a2e376e8856c916d9baa01f2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702615"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>如何：將類別分割成部分類別 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 `Partial` 關鍵字 (在 Visual Basic 中) 或使用 `partial` 關鍵字 (在 Visual C# 中)，將類別或結構的宣告分割成數個宣告。 您可以在任意數目的不同原始程式檔或在一個原始程式檔中，使用任意數目的部分宣告。 不過，所有宣告都必須位於相同的組件和相同的命名空間中。  
  
 部分類別適用於數種情況。 例如在處理大型專案時，將類別分割成多個檔案，可讓多位程式設計師同時處理該專案。 當您使用 Visual Studio 產生的程式碼時，不必重新建立原始程式檔即可變更類別  (Visual Studio 產生的程式碼範例包括 Windows Forms 和 Web 服務包裝函式程式碼)。因此，您可以建立使用自動產生類別的程式碼，而不必修改 Visual Studio 建立的檔案。  
  
 部分方法有兩種。 在 Visual C# 中，稱為 declaring (宣告) 和 implementing (實作)；在 Visual Basic 中則稱為 declaration (宣告) 和 implementation (實作)。  
  
 類別設計工具支援部分類別和方法。 類別圖表中的類型圖形即為部分方法的單一宣告位置。 如果部分類別在多個檔案中定義，您可以指定類別設計工具要使用哪個宣告位置，方法是設定 [屬性] 視窗中 [新的成員位置] 屬性。 也就是說，當您按兩下類別圖形時，類別設計工具會導向依 [新的成員位置] 屬性識別、包含類別宣告的原始程式檔。 當您按兩下類別圖形中的部分方法時，類別設計工具會導向部分方法宣告。 另外，在 [屬性] 視窗中，[檔案名稱] 屬性是指宣告位置。 若是部分類別，[檔案名稱] 會列出所有包含該類別宣告和實作程式碼的檔案。 但若是部分方法，[檔案名稱] 只會列出包含部分方法宣告的檔案。  
  
 下列範例會將 `Employee` 類別的定義分割成兩個宣告，兩者各自定義不同的程序。 範例中的兩個部分定義可位於一個原始程式檔或兩個不同的原始程式檔中。  
  
> [!NOTE]
> Visual Basic 使用 partial-class 定義，將 Visual Studio 產生的程式碼從使用者撰寫的程式碼分割出來。 程式碼會分成不相關的原始程式檔。 例如，[Windows Form 設計工具] 會定義控制項的部分類別，如 `Form`。 您不應該在這些控制項中修改產生的程式碼。  
  
 如需 Visual Basic 中部分類型的詳細資訊，請參閱 [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)。  
  
## <a name="example"></a>範例  
 若要分割 Visual Basic 中的類型定義，請使用 `Partial` 關鍵字，如下列範例所示。  
  
```vb  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## <a name="example"></a>範例  
 若要分割 Visual C# 中的類型定義，請使用 `partial` 關鍵字，如下列範例所示。  
  
```csharp  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [部分類別和方法](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)   
 [partial (類型)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)   
 [partial (方法) (C# 參考)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137)   
 [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
