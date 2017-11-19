---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: "重新命名重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eba5a9f55e5d3d08eee48dc083a7e2f848118162
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="rename-refactoring-c"></a>重新命名重構 (C#)
**重新命名**是最簡單的方式來重新命名識別項程式碼的符號，例如欄位、 區域變數、 方法、 命名空間、 屬性和類型的 Visual Studio 整合式的開發環境 (IDE) 的重構功能。 **重新命名**可以用來變更的註解，並在字串中的名稱，以及變更宣告及呼叫的識別項。  
  
> [!NOTE]
>  適用於 Visual Studio 使用原始檔控制，取得最新版本的來源，再重新執行 重新命名重構。  
  
 重新命名重構是可從下列 Visual Studio 功能：  
  
|功能|在 IDE 中重構的行為|  
|-------------|----------------------------------------|  
|程式碼編輯器|在程式碼編輯器中，重新命名重構時可使用您將游標放在特定類型的程式碼的符號。 在這個位置中的資料指標時，您可以叫用**重新命名**命令藉由輸入鍵盤快速鍵 （Ctrl + R、 Ctrl + R），或選取**重新命名**命令的快速動作，捷徑功能表，或**重構**功能表。|  
|類別檢視|當您在 類別檢視選取之識別項時，重新命名重構功能可從快顯功能表和**重構**功能表。|  
|物件瀏覽器|當您在物件瀏覽器選取識別項時，重新命名重構功能只可從**重構**功能表。|  
|屬性方格的 Windows Form 設計工具|在**屬性方格**的 Windows Form 設計工具中，在變更控制項的名稱將會起始重新命名作業，該控制項。 **重新命名**對話方塊不會出現。|  
|底下提供說明，包括方案總管|在**方案總管 中**、**重新命名**都能使用快顯功能表命令。 如果選取的來源檔案包含其名稱會與檔案名稱相同的類別，您可以使用此命令，同時重新命名來源檔案，並執行重新命名重構。<br /><br /> 例如，如果您建立的預設 Windows 型應用程式，然後重新命名 TestForm.cs Form1.cs Form1.cs 會變更為 TestForm.cs 和 Form1 類別的來源檔案名稱以及所有參考類別，將會重新命名為 TestForm。 **注意：** **復原**命令 (CTRL + Z) 只會復原重新命名重構程式碼中，並將的變更回原始名稱的檔案名稱。 <br /><br /> 如果選取的來源檔案不包含的類別，其名稱是與檔案名稱，相同**重新命名**命令**方案總管 中**只會重新命名來源檔案，而不會執行重新命名重構作業。|  
  
## <a name="rename-operations"></a>重新命名作業  
 當您執行**重新命名**，重構引擎會執行重新命名作業的每個程式碼的符號下, 表中所述。  
  
|程式碼符號|重新命名作業|  
|-----------------|----------------------|  
|欄位|變更為新名稱的宣告和使用方式的欄位。|  
|區域變數|變更為新名稱的宣告和變數的使用方式。|  
|方法|方法和所有參考該方法的名稱變更為新的名稱。 **注意：**當您重新命名的擴充方法時，重新命名作業會傳播至所有執行個體的方法在範圍內，不論是否為靜態方法或執行個體方法使用擴充方法。 如需詳細資訊，請參閱[擴充方法](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)。|  
|命名空間|命名空間的名稱變更為新的名稱，在宣告中，所有`using`陳述式，以及完整限定的名稱。 **注意：**時重新命名為命名空間，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]也會更新**預設命名空間**屬性**應用程式**頁面**專案設計工具**. 這個屬性不能重設選取**復原**從**編輯**功能表。 若要重設**預設命名空間**屬性值，您必須修改中的屬性**專案設計工具**。 如需詳細資訊，請參閱[應用程式頁面](../ide/reference/application-page-project-designer-csharp.md)。|  
|屬性|變更為新名稱的宣告和使用方式的屬性。|  
|類型|所有的宣告和類型的所有使用變成新的名稱，包括建構函式和解構函式。 針對部分類型，重新命名作業將會傳播到所有組件。|  
  
#### <a name="to-rename-an-identifier"></a>若要重新命名識別項  
  
1.  建立名為 `RenameIdentifier` 的主控台應用程式，再以下列程式碼取代 `Program`。  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  將游標置於`MethodB`，有兩種方法宣告或方法呼叫。  
  
3.  從**重構**功能表上，選取**重新命名**。 **重新命名** 對話方塊隨即出現。  
  
     您也可以以滑鼠右鍵按一下資料指標，指向 [**重構**操作功能表，然後按一下**重新命名**顯示**重新命名**] 對話方塊。  
  
4.  在**新名稱**欄位中，輸入`MethodC`。  
  
5.  選取**註解中的搜尋**核取方塊。  
  
6.  按一下 [確定]。  
  
7.  在**預覽變更**對話方塊中，按一下 **套用**。  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>若要重新命名識別項使用的快速動作  
  
1.  建立名為 `RenameIdentifier` 的主控台應用程式，再以下列程式碼取代 `Program`。  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  宣告中`MethodB`中，輸入或 backspace 鍵方法識別項。 快速動作將會出現燈泡邊界。  
  
    > [!NOTE]
    >  您可以只叫用重新命名重構在識別項宣告中使用的快速動作。  
  
3.  輸入鍵盤快速鍵**Shift + Alt + F10**以顯示 [快速動作] 功能表。  
  
     -或-  
  
     按一下以顯示 [快速動作] 功能表的燈泡旁邊的黑色三角形。  
  
4.  選取**重新命名 '\<identifer1 >' 到'\<identifier2 >'**叫用 重新命名重構的功能表項目。 所有參考 **\<identifer1 >**自動更新為 **\<identifier2 >**。  
  
## <a name="remarks"></a>備註  
  
## <a name="renaming-implemented-or-overridden-members"></a>重新命名實作或覆寫的成員  
 當您**重新命名**實作/覆寫或是實作/的成員覆寫在其他類型的成員[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]顯示對話方塊，指出重新命名作業會造成串聯更新。 如果您按一下**繼續**、 重構引擎以遞迴方式尋找並重新命名基底中的所有成員和衍生的型別具有實作/覆寫關聯性，以重新命名的成員。  
  
 下列程式碼範例包含具有實作/覆寫的關聯性的成員。  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 在上述範例中，重新命名`C.Method()`也會重新命名`Ibase.Method()`因為`C.Method()`實作`Ibase.Method()`。 接下來，重構引擎以遞迴方式查出`Ibase.Method()`藉由`Derived.Method()`並將重新命名`Derived.Method()`。 並不會重新命名重構引擎`Base.Method()`，因為`Derived.Method()`不會覆寫`Base.Method()`。 重構引擎會在這裡停止除非您有**重新命名多載**簽入**重新命名** 對話方塊。  
  
 如果**重新命名多載**勾選，重新命名重構引擎`Derived.Method(int i)`因為其多載`Derived.Method()`，`Base.Method(int i)`因為它會覆寫`Derived.Method(int i)`，和`Base.Method()`因為它是多載`Base.Method(int i)`.  
  
> [!NOTE]
>  當您重新命名參考的組件中定義的成員時，對話方塊會說明重新命名將會導致建置錯誤。  
  
## <a name="renaming-properties-of-anonymous-types"></a>重新命名匿名類型的屬性  
 當您重新命名匿名型別中的屬性時，重新命名作業將會傳播到其他具有相同屬性的匿名型別中的屬性。 下列範例將說明此行為。  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 在上述程式碼中，重新命名`ID`會變更`ID`中兩個陳述式因為它們具有相同的基礎匿名型別。  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 在上述程式碼中，重新命名`ID`只會重新命名的一個執行個體`ID`因為`companyIDs`和`orderIDs`沒有相同的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](refactoring-csharp.md)   
 [匿名類型](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)