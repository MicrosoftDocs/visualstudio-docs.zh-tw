---
title: 合併 VBA 和檔層級自訂
description: 瞭解如何在 Microsoft Office Word 或 Excel 的檔層級自訂一部分的檔中，使用 Visual Basic for Applications (VBA) 程式碼。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1c5f66042dad7051c856aa6158ea0a666a81e9b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938521"
---
# <a name="combine-vba-and-document-level-customizations"></a>合併 VBA 和檔層級自訂
  您可以在屬於 Microsoft Office Word 或 Microsoft Office Excel 文件層級自訂的文件中使用 Visual Basic for Applications (VBA) 程式碼。 您可以在來自自訂組件的文件中呼叫 VBA 程式碼，或者可以設定專案，讓文件中的 VBA 程式碼可以呼叫自訂組件中的程式碼。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>檔層級自訂中 VBA 程式碼的行為
 當您在 Visual Studio 中開啟您的專案時，是在設計模式中開啟文件。 當文件處於設計模式中時，VBA 程式碼不會執行，因此您可以處理文件和程式碼，而不會執行 VBA 程式碼。

 當您執行方案時，VBA 和自訂組件中的事件處理常式都會拾取文件中引發的事件，且兩組程式碼都會執行。 您不能事先決定哪一個程式碼會比其他程式碼先執行；您必須透過測試個別的案例來得知。 如果兩組程式碼並未經過小心地協調及測試，您可能會得到非預期的結果。

## <a name="call-vba-code-from-the-customization-assembly"></a>從自訂群組件呼叫 VBA 程式碼
 您可以在 Word 文件中呼叫巨集，以及在 Excel 活頁簿中呼叫巨集和函式。 若要執行此工作，請使用下列的其中一個方法：

- 對於 Word，請呼叫 <xref:Microsoft.Office.Interop.Word._Application.Run%2A> 類別的方法 <xref:Microsoft.Office.Interop.Word.Application> 。

- 對於 Excel，請呼叫 <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> 類別的 <xref:Microsoft.Office.Interop.Excel.Application> 方法。

  針對每個方法中，第一個參數會識別您想要呼叫的巨集或函式，而其餘的選擇性參數則指定要傳遞至巨集或函式的參數。 第一個參數可以針對 Word 和 Excel 有不同的格式：

- 針對 Word，第一個參數是字串，它可以是範本、模組和巨集名稱的任何組合。 如果您指定文件名稱，您的程式碼只能在與目前內容相關的文件中而不是任何文件中的任何巨集中執行巨集。

- 針對 Excel，第一個參數可以是字串，指定巨集名稱、用來表示函式所在位置的 <xref:Microsoft.Office.Interop.Excel.Range> ，或已註冊的 DLL (XLL) 函式的註冊 ID。 如果您傳遞字串，將會在使用中工作表的內容中評估該字串。

  下列程式碼範例顯示如何針對 Excel 從文件層級的專案呼叫名為 `MyMacro` 的巨集。 這個範例假設 `MyMacro` 定義於 `Sheet1`。

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> 如需在 `missing` Visual c # 中使用全域變數來取代選用參數的相關資訊，請參閱在 [Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)。

## <a name="call-code-in-document-level-customizations-from-vba"></a>從 VBA 呼叫檔層級自訂中的程式碼
 您可以設定 Word 或 Excel 的文件層級專案，讓文件中的 Visual Basic for Applications (VBA) 程式碼可以呼叫自訂組件中的程式碼。 這在下列案例中很有用：

- 您想要使用與相同文件相關聯的文件層級自訂中的功能，來擴充文件中的現有 VBA 程式碼。

- 您想要，藉由在文件中撰寫 VBA 程式碼，讓您在文件層級自訂中開發的服務，能供可以存取服務的使用者使用。

  Visual Studio 中的 Office 開發工具為 VSTO 增益集提供類似的功能。如果您要開發 VSTO 增益集，可以從其他 Microsoft Office 的解決方案呼叫 VSTO 增益集中的程式碼。 如需詳細資訊，請參閱 [從其他 Office 方案呼叫 VSTO 增益集](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)的程式碼。

> [!NOTE]
> 這項功能無法用於 Word 範本專案。 它只能在 Word 文件、Excel 活頁簿或 Excel 範本專案中使用。

## <a name="requirements"></a>規格需求
 您的專案必須符合下列需求，您才能啟用 VBA 程式碼以呼叫自訂組件：

- 文件必須具有下列其中一個副檔名：

  - 針對 Word： *. docm* 或 *.doc*

  - 適用于 Excel： *. xlsm*、 *. xltm*、 *.xls* 或 *.xlt*

- 文件必須已經包含有 VBA 程式碼存在的 VBA 專案。

- 必須允許文件中的 VBA 程式碼執行，而不提示使用者啟用巨集。 您可以將 Office 專案的位置加入 Word 或 Excel 信任中心設定的信任位置清單，以信任 VBA 程式碼執行。

- Office 專案必須包含至少一個公用類別，其中包含一或多個要公開給 VBA 的公用成員。

     您可以公開方法、屬性和事件給 VBA。 您所公開的類別可以是主項目類別 (例如 Word 的 `ThisDocument` ，或 Excel 的 `ThisWorkbook` 和 `Sheet1` ) 或您在專案中定義的另一個類別。 如需主專案的詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>讓 VBA 程式碼呼叫自訂群組件
 有兩種不同的方式，您可以將自訂組件中的成員公開給文件中的 VBA 程式碼：

- 您可以將 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案中的主項目類別成員公開給 VBA。 若要這樣做，請在設計工具中開啟主項目 (也就是文件、工作表或活頁簿) 時，在 [屬性]  視窗中將主項目的 **EnableVbaCallers** 屬性設為 **True** 。 Visual Studio 會自動執行所有必要工作，讓 VBA 程式碼能呼叫類別的成員。

- 您可以在 Visual C# 專案中將任何公用類別中的成員公開給 VBA，或在 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案中將非主項目類別中的成員公開給 VBA。 此選項可讓您更彈性地選擇要公開給 VBA 的類別，但它也需要更多的手動步驟。

   若要這樣做，您必須執行下列主要步驟：

  1. 將類別公開給 COM。

  2. 覆寫專案中之主項目類別的 **GetAutomationObject** 方法，傳回您正在公開給 VBA 之類別的執行個體。

  3. 將專案中任何主項目類別的 **ReferenceAssemblyFromVbaProject** 屬性設為 **True**。 這樣會將自訂組件的類型程式庫內嵌至組件，並將類型程式庫的參考加入文件中的 VBA 專案。

  如需詳細指示，請參閱 [如何：公開程式碼給 Visual Basic 專案中的 vba](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) 和 [如何：將程式碼公開給 Visual C&#35; 專案中的 vba](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)。

  **EnableVbaCallers** 和 **ReferenceAssemblyFromVbaProject** 屬性都只在設計階段的 [屬性]  視窗使用，不能用在執行階段。 若要檢視屬性，請在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]開啟主項目的設計工具。 如需有關設定這些屬性時 Visual Studio 執行之特定工作的詳細資訊，請參閱 [主專案屬性所執行](#PropertyTasks)的工作。

> [!NOTE]
> 如果活頁簿或文件尚未包含 VBA 程式碼，或文件中的 VBA 程式碼不受信任而無法執行，當您將 **EnableVbaCallers** 或 **ReferenceAssemblyFromVbaProject** 屬性設為 **True** 時會收到錯誤訊息。 這是因為在這種情況中，Visual Studio 無法修改文件中的 VBA 專案。

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>使用 VBA 程式碼中的成員呼叫自訂群組件
 在您設定專案以讓 VBA 程式碼呼叫自訂組件之後，Visual Studio 會將下列成員加入文件中的 VBA 專案：

- 對於所有的專案，Visual Studio 會加入名為 `GetManagedClass`的全域方法。

- 對於 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 您使用 **EnableVbaCallers** 屬性公開主專案類別成員的專案，Visual Studio 也會將名為的屬性加入 `CallVSTOAssembly` 至 `ThisDocument` `ThisWorkbook` `Sheet1` VBA 專案中的、、、 `Sheet2` 或 `Sheet3` 模組。

  您可以使用 `CallVSTOAssembly` 屬性或 `GetManagedClass` 方法來存取您公開給專案中之類別的公用成員。

> [!NOTE]
> 在您開發並部署方案時，有幾份不同的文件可以讓您加入 VBA 程式碼。 如需詳細資訊，請參閱 [將 VBA 程式碼加入檔的指導方針](#Guidelines)。

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>在 Visual Basic 專案中使用 CallVSTOAssembly 屬性
 使用 `CallVSTOAssembly` 屬性來存取您加入主項目類別的公用成員。 例如，下列 VBA 巨集會呼叫名為 `MyVSTOMethod` 的方法，它定義於 Excel 活頁簿專案中的 `Sheet1` 類別。

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 這個屬性比直接使用 `GetManagedClass` 方法，在呼叫自訂組件時更方便。 `CallVSTOAssembly` 會傳回代表您公開給 VBA 之主項目類別的物件。 傳回物件的成員和方法參數會出現在 IntelliSense 中。

 `CallVSTOAssembly` 屬性具有類似下列程式碼的宣告。 此程式碼假設您已在名為 `Sheet1` 的 Excel 活頁簿專案中，將 `ExcelWorkbook1` 主項目類別公開給 VBA。

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>使用 GetManagedClass 方法
 若要使用全域 `GetManagedClass` 方法，請傳入對應至主項目類別的 VBA 物件，此類別包含 **GetAutomationObject** 方法的覆寫。 然後，使用傳回的物件來存取公開給 VBA 的類別。

 例如，下列 VBA 巨集會呼叫名為 `MyVSTOMethod` 的方法，它定義於名為 `Sheet1` 的 Excel 活頁簿專案中的 `ExcelWorkbook1`主項目類別。

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 `GetManagedClass` 方法具有下列宣告。

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 此方法會傳回代表您公開給 VBA 之類別的物件。 傳回物件的成員和方法參數會出現在 IntelliSense 中。

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> 將 VBA 程式碼加入檔的指導方針
 有數份不同的文件，您可以在其中加入呼叫文件層級自訂的 VBA 程式碼。

 當您開發並測試方案時，可以在文件中撰寫 VBA 程式碼，當您在 Visual Studio 中偵錯或執行您的專案時就會開啟此文件 (也就是在組建輸出資料夾中的文件)。 不過，您加入此文件的任何 VBA 程式碼將會在下一次建置專案時被覆寫，因為 Visual Studio 會將組建輸出資料夾中的文件取代為來自主要專案資料夾的文件複本。

 如果您想要在偵錯或執行方案時儲存您加入文件的 VBA 程式碼，請將 VBA 程式碼複製到專案資料夾中的文件。 如需組建程式的詳細資訊，請參閱 [建立 office 方案](../vsto/building-office-solutions.md)。

 當您準備好要部署方案時，有三個主要的文件位置，您可以在其中加入 VBA 程式碼。

### <a name="in-the-project-folder-on-the-development-computer"></a>在開發電腦上的專案資料夾中
 如果您對文件中的 VBA 程式碼和自訂程式碼具有完整控制權，則這個位置很方便。 因為文件是在開發電腦上，如果您變更自訂程式碼，便可以輕易修改 VBA 程式碼。 當您建置、偵錯和發行方案時，您加入這份文件的 VBA 程式碼會保留在文件中。

 在設計工具中開啟文件時，您無法將 VBA 程式碼加入文件。 您必須先在設計工具中關閉文件，然後直接在 Word 或 Excel 中開啟文件。

> [!CAUTION]
> 如果您加入在文件開啟時執行的 VBA 程式碼，在少數情況下這段程式碼可能會損毀文件或導致它無法在設計工具中開啟。

### <a name="in-the-publish-or-installation-folder"></a>在 [發行] 或 [安裝] 資料夾中
 在某些情況下，可能適合將 VBA 程式碼加入至發行或安裝資料夾中的文件。 例如，如果 VBA 程式碼是由不同開發人員在未安裝 Visual Studio 的電腦上撰寫並測試，您可能會選擇這個選項。

 如果使用者直接從發行資料夾安裝方案，每次發行方案時您都必須將 VBA 程式碼加入文件。 當您發行方案時，Visual Studio 會覆寫發行位置中的文件。

 如果使用者從不同於發行資料夾的安裝資料夾安裝方案，您就不用每次發行方案時都將 VBA 程式碼加入文件。 準備好將發行更新從發行資料夾移到安裝資料夾時，請將所有檔案複製到文件以外的安裝資料夾。

### <a name="on-the-end-user-computer"></a>在終端使用者電腦上
 如果使用者是呼叫您在文件層級自訂中提供之服務的 VBA 開發人員，您可以告訴他們如何在他們的文件複本中使用 `CallVSTOAssembly` 屬性或 `GetManagedClass` 方法呼叫您的程式碼。 當您將更新發佈至方案時，將不會覆寫終端使用者電腦上檔中的 VBA 程式碼，因為發行更新不會修改檔。

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> 主專案屬性執行的工作
 當您使用 **EnableVbaCallers** 和 **ReferenceAssemblyFromVbaProject** 屬性時，Visual Studio 會執行不同的工作集。

### <a name="enablevbacallers"></a>EnableVbaCallers
 當您在 Visual Basic 專案中將主項目的 **EnableVbaCallers** 屬性設為 **True** ，Visual Studio 會執行下列工作：

1. 它會將 <xref:Microsoft.VisualBasic.ComClassAttribute> 和 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性加入主項目類別。

2. 它會覆寫主項目類別的 **GetAutomationObject** 方法。

3. 它會將主項目的 **ReferenceAssemblyFromVbaProject** 屬性設為 **True**。

   當您將 **EnableVbaCallers** 屬性設回 **False** 時，Visual Studio 會執行下列工作：

4. 它會從 <xref:Microsoft.VisualBasic.ComClassAttribute> 類別移除 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 和 `ThisDocument` 屬性。

5. 它會從主項目類別移除 **GetAutomationObject** 方法。

   > [!NOTE]
   > Visual Studio 不會自動將 **ReferenceAssemblyFromVbaProject** 屬性設回 **False**。 您可以使用 [屬性]  視窗，手動將此屬性設定為 **False** 。

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 當 Visual Basic 或 Visual C# 專案中的任何主項目的 **ReferenceAssemblyFromVbaProject** 屬性設為 **True** 時，Visual Studio 會執行下列工作：

1. 它會為自訂組件產生類型程式庫，並將類型程式庫內嵌在組件中。

2. 它會在文件中的 VBA 專案加入下列類型程式庫的參考：

   - 自訂組件的類型程式庫。

   - Microsoft Visual Studio Tools for Office Execution Engine 9.0 類型程式庫。 這個類型程式庫已包括在 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]中。

   當 **ReferenceAssemblyFromVbaProject** 屬性設回 **False** 時，Visual Studio 會執行下列工作：

3. 它會從文件中的 VBA 專案移除類型程式庫參考。

4. 它會從組件移除內嵌的類型程式庫。

## <a name="troubleshoot"></a>疑難排解
 下表列出一些常見的錯誤與錯誤修正建議。

|錯誤|建議|
|-----------|----------------|
|設定 **EnableVbaCallers** 或 **ReferenceAssemblyFromVbaProject** 屬性之後，會有錯誤訊息指出文件不包含 VBA 專案，或是您的權限不足，無法存取文件中的 VBA 專案。|請確定專案中的文件包含至少一個 VBA 巨集、VBA 專案擁有足夠的信任可以執行，而且 VBA 專案未受到密碼保護。|
|設定 **EnableVbaCallers** 或 **ReferenceAssemblyFromVbaProject** 屬性之後，會有錯誤訊息指出 <xref:System.Runtime.InteropServices.GuidAttribute> 宣告遺漏或已損毀。|請確認宣告 <xref:System.Runtime.InteropServices.GuidAttribute> 位於您專案中的 *AssemblyInfo.cs* 或 *AssemblyInfo .vb* 檔案，而且此屬性已設定為有效的 GUID。|
|設定 **EnableVbaCallers** 或 **ReferenceAssemblyFromVbaProject** 屬性之後，會有錯誤訊息指出 <xref:System.Reflection.AssemblyVersionAttribute> 所指定版本號碼無效。|確定 <xref:System.Reflection.AssemblyVersionAttribute> 專案中的 *AssemblyInfo.cs* 或 *AssemblyInfo .vb* 檔案中的宣告已設定為有效的元件版本號碼。 如需組件版本號碼的相關資訊，請參閱 <xref:System.Reflection.AssemblyVersionAttribute> 類別。|
|重新命名自訂組件之後，呼叫自訂組件的 VBA 程式碼會停止運作。|如果您在將自訂組件名稱公開給 VBA 程式碼之後才變更它，文件中的 VBA 專案與自訂組件之間的連結已中斷。 若要修正此問題，請將專案中的 **ReferenceFromVbaAssembly** 屬性變更為 **False** ，然後再變回 **True**，最後將 VBA 程式碼中的任何舊組件名稱參考取代為新的組件名稱。|

## <a name="see-also"></a>另請參閱
- [如何：將程式碼公開給 Visual Basic 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [如何：將程式碼公開給 Visual C&#35; 專案中的 VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [逐步解說：在 Visual Basic 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [逐步解說：在 Visual C&#35; 專案中呼叫 VBA 的程式碼](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Visual Studio 中的 VBA 和 Office 方案比較](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [程式檔層級自訂](../vsto/programming-document-level-customizations.md)
