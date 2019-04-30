---
title: 重新命名重構 (C#) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 971ca4e94f28016335483a03f4b0121de587f00d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439962"
---
# <a name="rename-refactoring-c"></a>重新命名重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**重新命名**是 Visual Studio 的整合式的開發環境 (IDE) 可輕鬆地重新命名程式碼符號，例如欄位、 區域變數、 方法、 命名空間、 屬性和類型的識別項的重構功能。 **重新命名**可用變更的註解中，並在字串中的名稱，以及變更的宣告和呼叫的識別項。  
  
> [!NOTE]
> 適用於 Visual Studio 中使用原始檔控制，取得最新版本的來源，再重新執行 重新命名重構。  
  
 重新命名重整功能是可從下列 Visual Studio 功能：  
  
|功能|在 IDE 中重構的行為|  
|-------------|----------------------------------------|  
|程式碼編輯器|當您將游標放在特定類型的程式碼符號，則在程式碼編輯器中，重新命名重構時使用。 在這個位置中的資料指標時，您可以叫用**重新命名**命令輸入鍵盤快速鍵 （CTRL + R、 CTRL + R），或選取**重新命名**命令從捷徑功能表或智慧標籤**重構**功能表。|  
|類別檢視|當您在 類別檢視選取的識別項時，重新命名重構是可以從捷徑功能表並**重構**功能表。|  
|物件瀏覽器|當您在物件瀏覽器中選取一個識別項時，重新命名重整，但只能透過**重構**功能表。|  
|屬性方格的 Windows Form 設計工具|在 **屬性方格**的 Windows Form 設計工具中，在變更控制項的名稱將會起始重新命名作業，該控制項。 **重新命名**對話方塊不會出現。|  
|底下提供說明，包括方案總管|在**方案總管 中**，則**重新命名**命令是可用的捷徑功能表上。 如果選取的來源檔案包含的類別名稱為檔案名稱相同的類別，您可以使用此命令，以同時重新命名原始程式檔，並執行重新命名重構。<br /><br /> 比方說，如果您建立的預設 Windows 架構應用程式，然後將 Form1.cs 重新命名為 TestForm.cs Form1.cs 會變更為 TestForm.cs 和 Form1 類別原始程式檔名稱和所有參考類別，將重新命名為 TestForm。 **注意：** **復原**命令 (CTRL + Z) 只會在復原重新命名重構程式碼中，並會的變更回原始名稱的檔案名稱。 <br /><br /> 如果選取的來源檔案不包含其名稱為檔案名稱，相同的類別**重新命名**命令**方案總管 中**只會重新命名原始程式檔，而不會執行重新命名重構。|  
  
## <a name="rename-operations"></a>重新命名作業  
 當您執行**重新命名**，重構引擎會執行重新命名作業的每個程式碼的符號下, 表中所述。  
  
|程式碼符號|重新命名作業|  
|-----------------|----------------------|  
|欄位|變更欄位的使用方式與宣告新的名稱。|  
|本機變數|變更為新名稱的宣告和使用方式的變數。|  
|方法|變更方法的名稱和該方法的所有參考新的名稱。 **注意：** 當您重新命名的擴充方法時，重新命名作業會傳播至所有執行個體的方法在範圍內，不論是否使用擴充方法作為靜態方法或執行個體方法中。 如需詳細資訊，請參閱[擴充方法](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51)。|  
|命名空間|命名空間的名稱變更為新的名稱，在宣告中，所有`using`陳述式，以及完整限定的名稱。 **注意：** 重新命名的命名空間時[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]也會更新**預設命名空間**上的屬性**應用程式**頁面**專案設計工具**。 這個屬性不能重設，方法是選取**恢復**從**編輯**功能表。 若要重設**預設命名空間**屬性值，您必須修改中的屬性**專案設計工具**。 如需詳細資訊，請參閱 <<c0> [ 應用程式頁面](../ide/reference/application-page-project-designer-csharp.md)。|  
|屬性|變更為新名稱的宣告和使用方式的屬性。|  
|類型|變更為新的名稱，包括建構函式和解構函式的所有宣告和類型的所有使用方式。 針對部分類型，重新命名作業會傳播到所有的組件。|  
  
#### <a name="to-rename-an-identifier"></a>若要重新命名識別項  
  
1. 建立名為 `RenameIdentifier` 的主控台應用程式，再以下列程式碼取代 `Program`。  
  
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
  
2. 將游標置於`MethodB`，方法宣告或方法呼叫。  
  
3. 從**重構**功能表上，選取**重新命名**。 **重新命名** 對話方塊隨即出現。  
  
     您也可以以滑鼠右鍵按一下資料指標，指向**重構**操作功能表，然後按一下**重新命名**以顯示**重新命名** 對話方塊。  
  
4. 在 **新的名稱**欄位中，輸入`MethodC`。  
  
5. 選取 **註解中的搜尋**核取方塊。  
  
6. 按一下 [確定] 。  
  
7. 在 [**預覽變更**] 對話方塊中，按一下**套用**。  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>若要重新命名識別項使用智慧標籤  
  
1. 建立名為 `RenameIdentifier` 的主控台應用程式，再以下列程式碼取代 `Program`。  
  
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
  
2. 宣告中`MethodB`中，輸入或 backspace 鍵方法識別項。 這個識別項下方會出現智慧標籤提示。  
  
    > [!NOTE]
    > 此外，您只可以叫用重新命名重整智慧標籤使用的識別項宣告。  
  
3. 輸入鍵盤快速鍵 SHIFT + ALT + F10，然後按 向下箭號顯示智慧標籤功能表。  
  
     -或-  
  
     滑鼠指標移顯示智慧標籤的智慧標籤提示。 然後將滑鼠指標移的智慧標籤，然後按一下向下箭號顯示智慧標籤功能表。  
  
4. 選取 **重新命名 '\<identifer1 >' 到'\<identifier2 >'** 叫用重新命名重整，而不變更程式碼預覽的功能表項目。 所有參考 **\<identifer1 >** 將自動更新為 **\<identifier2 >**。  
  
     -或-  
  
     選取 **重新命名預覽**功能表項目以叫用重新命名重構預覽您的程式碼的變更。 **預覽變更**對話方塊會隨即出現。  
  
## <a name="remarks"></a>備註  
  
## <a name="renaming-implemented-or-overridden-members"></a>重新命名已實作或覆寫成員  
 當您**重新命名**實作/覆寫或會實作/覆寫在其他類型中，成員的成員[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]顯示對話方塊，指出重新命名作業會導致階層式更新。 如果您按一下**繼續**、 重構引擎以遞迴方式尋找並重新命名在基底中的所有成員和衍生的類型的實作/覆寫的關聯性要重新命名的成員。  
  
 下列程式碼範例包含具有實作/覆寫的關聯性的成員。  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 在上述範例中，重新命名`C.Method()`也會重新命名`Ibase.Method()`因為`C.Method()`實作`Ibase.Method()`。 接下來，重構引擎以遞迴方式會看到所`Ibase.Method()`藉由`Derived.Method()`，然後重新命名`Derived.Method()`。 重構引擎不會重新命名`Base.Method()`，因為`Derived.Method()`未覆寫`Base.Method()`。 重構引擎會在這裡停止除非您有**重新命名多載**簽入**重新命名** 對話方塊。  
  
 如果**重新命名多載**勾選，重新命名重構引擎`Derived.Method(int i)`因為它多載`Derived.Method()`，`Base.Method(int i)`因為它會覆寫`Derived.Method(int i)`，和`Base.Method()`因為它的多載`Base.Method(int i)`.  
  
> [!NOTE]
> 當您重新命名參考的組件中所定義的成員時，對話方塊會說明重新命名會造成建置錯誤。  
  
## <a name="renaming-properties-of-anonymous-types"></a>重新命名匿名型別的屬性  
 當您重新命名匿名型別中的屬性時，重新命名作業將會傳播至其他具有相同屬性的匿名型別中的屬性。 下列範例說明此行為。  
  
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
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)   
 [匿名類型](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)