---
title: 重新命名重構C#（） |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667483"
---
# <a name="rename-refactoring-c"></a>重新命名重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[**重新命名**] 是 Visual Studio 整合式開發環境（IDE）中的重構功能，可讓您輕鬆地重新命名程式碼符號（例如欄位、區域變數、方法、命名空間、屬性和類型）的識別碼。 [**重新命名**] 可以用來變更批註和字串中的名稱，以及變更識別碼的宣告和呼叫。

> [!NOTE]
> 使用 Visual Studio 的原始檔控制時，請取得最新版本的來源，然後再嘗試執行重新命名重構。

 重新命名重構可從下列 Visual Studio 功能取得：

|特殊功能|IDE 中重構的行為|
|-------------|----------------------------------------|
|程式碼編輯器|在 [程式碼編輯器] 中，當您將游標放在特定類型的程式碼符號上時，可以使用 [重新命名重構]。 當游標在此位置時，您可以藉由輸入鍵盤快速鍵（CTRL + R、CTRL + R），或從智慧標籤、快捷方式功能表或 [**重構**] 功能表選取 [**重新命名**] 命令來叫用 [**重新**命名] 命令。|
|類別檢視|當您在類別檢視中選取識別碼時，會從快捷方式功能表和 [**重構**] 功能表中取得重新命名重構。|
|物件瀏覽器|當您在物件瀏覽器中選取識別碼時，只能從 [**重構**] 功能表使用 [重新命名重構]。|
|Windows Form 設計工具的屬性方格|在 Windows Form 設計工具的**屬性方格**中，變更控制項的名稱將會起始該控制項的重新命名作業。 [**重新命名**] 對話方塊將不會出現。|
|底下提供說明，包括方案總管|在**方案總管**中，可在快捷方式功能表上使用 [**重新命名**] 命令。 如果選取的來源檔案包含類別名稱與檔案名相同的類別，您可以使用這個命令同時重新命名來源檔案，並執行重新命名重構。<br /><br /> 例如，如果您建立預設的 Windows 應用程式，然後將 Form1.cs 重新命名為 TestForm.cs，則來原始檔案名 Form1.cs 會變更為 TestForm.cs，而類別 Form1 和該類別的所有參考都將重新命名為 TestForm。 **注意：** [**復原**] 命令（CTRL + Z）只會復原程式碼中的重新命名重構，而且不會將檔案名變更回原始名稱。 <br /><br /> 如果選取的來源檔案不包含名稱與檔案名相同的類別，**方案總管**中的 [**重新命名**] 命令只會重新命名來源檔案，而且不會執行重新命名重構。|

## <a name="rename-operations"></a>重新命名作業
 當您執行**重新命名**時，重構引擎會針對每個程式碼符號執行特定的重新命名作業，如下表所述。

|程式碼符號|重新命名作業|
|-----------------|----------------------|
|欄位|將欄位的宣告和使用方式變更為新名稱。|
|區域變數|將變數的宣告和使用方式變更為新名稱。|
|方法|將方法的名稱和該方法的所有參考變更為新名稱。 **注意：** 當您重新命名擴充方法時，重新命名作業會傳播至範圍內方法的所有實例，而不論擴充方法是否當做靜態方法或實例方法使用。 如需詳細資訊，請參閱[擴充方法](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51)。|
|命名空間|將命名空間的名稱變更為宣告中的新名稱、所有 `using` 語句和完整限定名稱。 **注意：** 重新命名命名空間時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 也會更新 [**專案設計**工具] 之 [**應用程式**] 頁面上的 [**預設命名空間**] 屬性。 從 [**編輯**] 功能表選取 [**復原**]，就無法重設這個屬性。 若要重設 [**預設命名空間**] 屬性值，您必須在 [**專案設計**工具] 中修改屬性。 如需詳細資訊，請參閱[應用程式頁面](../ide/reference/application-page-project-designer-csharp.md)。|
|屬性|將屬性的宣告和使用方式變更為新名稱。|
|輸入|將類型的所有宣告和所有使用方式變更為新的名稱，包括函式和析構函式。 若為部分類型，重新命名作業將會傳播至所有元件。|

#### <a name="to-rename-an-identifier"></a>若要重新命名識別碼

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

2. 將游標放在 `MethodB` 上，不論是在方法宣告或方法呼叫中。

3. 從 [**重構**] 功能表中，選取 [**重新命名**]。 [**重新命名**] 對話方塊隨即出現。

     您也可以用滑鼠右鍵按一下游標，指向內容功能表上的 [**重構**]，然後按一下 [**重新命名**] 以顯示 [**重新命名**] 對話方塊。

4. 在 [**新名稱**] 欄位中，輸入 `MethodC`。

5. 選取 [**在批註中搜尋**] 核取方塊。

6. 按一下 [確定]。

7. 在 [**預覽變更**] 對話方塊中，**按一下 [** 套用]。

#### <a name="to-rename-an-identifier-using-smart-tags"></a>使用智慧標籤重新命名識別碼

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

2. 在 `MethodB` 的宣告中，于方法識別碼上輸入或倒退鍵。 智慧標籤提示會出現在此識別碼的下方。

    > [!NOTE]
    > 您只能在識別碼的宣告中使用智慧標籤叫用重新命名重構。

3. 輸入鍵盤快速鍵 SHIFT + ALT + F10，然後按向下箭號以顯示智慧標籤功能表。

     -或-

     將滑鼠指標移至智慧標籤提示上方，以顯示智慧標籤。 然後，將滑鼠指標移到智慧標籤上，然後按一下向下箭號以顯示智慧標籤功能表。

4. 選取 [將 **' \<identifer1 > ' 重新命名為 ' \<identifier2 >** ] 功能表項目，以叫用重新命名重構，而不預覽您的程式碼變更。 **@No__t_1identifer1 >** 的所有參考都會自動更新為 **\<identifier2 >** 。

     -或-

     選取 [**使用預覽重新命名**] 功能表項目，以使用程式碼變更的預覽來叫用重新命名重構。 [**預覽變更**] 對話方塊隨即出現。

## <a name="remarks"></a>備註

## <a name="renaming-implemented-or-overridden-members"></a>重新命名已執行或已覆寫的成員
 當您**重新命名**執行/覆寫的成員，或其他類型的成員所實/寫時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會顯示一個對話方塊，指出重新命名作業將會造成串聯式更新。 如果您按一下 [**繼續**]，重構引擎會以遞迴方式尋找並重新命名基底和衍生型別中的所有成員，該類型具有與要重新命名之成員的執行/覆寫關聯

 下列程式碼範例包含具有 implements/覆寫關聯性的成員。

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 在上述範例中，重新命名 `C.Method()` 也會將 `Ibase.Method()` 重新命名，因為 `C.Method()` 會執行 `Ibase.Method()`。 接下來，重構引擎會以遞迴方式看到 `Ibase.Method()` 是由 `Derived.Method()` 執行，並將 `Derived.Method()` 重新命名。 重構引擎不會重新命名 `Base.Method()`，因為 `Derived.Method()` 不會覆寫 `Base.Method()`。 除非您已在 [**重新命名**] 對話方塊中選取 [**重新命名**多載]，否則重構引擎會在此停止。

 如果已核取 [**重新命名**多載]，重構引擎會將 `Derived.Method(int i)` 重新命名，因為它會多載 `Derived.Method()`、`Base.Method(int i)`，因為它是由 `Derived.Method(int i)` 覆寫，而 `Base.Method()` 因為它是 `Base.Method(int i)` 的多載。

> [!NOTE]
> 當您重新命名在參考元件中定義的成員時，會有一個對話方塊說明重新命名會導致組建錯誤。

## <a name="renaming-properties-of-anonymous-types"></a>重新命名匿名型別的屬性
 當您重新命名匿名型別中的屬性時，重新命名作業將會傳播到其他具有相同屬性的匿名型別中的屬性。 下列範例將說明此行為。

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 在上述程式碼中，重新命名 `ID` 將會變更這兩個語句 `ID`，因為它們具有相同的基礎匿名型別。

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 在上述程式碼中，重新命名 `ID` 只會將一個 `ID` 的實例重新命名，因為 `companyIDs` 和 `orderIDs` 沒有相同的屬性。

## <a name="see-also"></a>請參閱
 [重構（C#）](../csharp-ide/refactoring-csharp.md) [匿名型別](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)