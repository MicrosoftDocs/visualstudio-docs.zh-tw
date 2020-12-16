---
title: 在 Office 方案中撰寫程式碼
description: 瞭解如何在 Microsoft Office 的方案中撰寫程式碼，並瞭解 Office 物件模型對 managed 程式碼的公開方式。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea589cb4406a383876b1f16721f18fc48ebadd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526027"
---
# <a name="write-code-in-office-solutions"></a>在 Office 方案中撰寫程式碼
  在 Office 專案中撰寫程式碼，在某些方面不同於撰寫 Visual Studio 中其他類型專案的程式碼。 其中有許多差異的原因與將 Office 物件模型公開給 Managed 程式碼的方式相關。 其他差異則與 Office 專案的設計相關。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Managed 程式碼與 Office 程式設計
 促成建立整合式 Microsoft Office 方案的重要技術是自動化功能，這是元件物件模型 (COM) 技術的一部分。 自動化可讓您使用程式碼來建立及控制任何應用程式公開的軟體物件、DLL 或支援適當程式設計介面的 ActiveX 控制項。

### <a name="understand-primary-interop-assemblies"></a>瞭解主要 interop 元件
 Microsoft Office 應用程式將其許多功能公開給自動化。 不過，您無法直接使用 Managed 程式碼 (例如 Visual Basic 或 C#) 來自動化 Office 應用程式。 若要使用 Managed 程式碼自動化 Office 應用程式，您必須使用 Office 主要 Interop 組件 (PIA)。 主要 Interop 組件可讓 Managed 程式碼與 Office 應用程式的 COM 物件模型互動。

 每個 Microsoft Office 應用程式都有 PIA。 當您在 Visual Studio 中建立 Office 專案時，適當的 PIA 的參考會自動加入專案。 若要自動化專案中的其他 Office 應用程式功能，您必須手動加入適當的 PIA 的參考。 如需詳細資訊，請參閱 [如何：透過主要 interop 元件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)。

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>在設計階段和執行時間使用主要 interop 元件
 您必須在開發電腦的全域組件快取內安裝並註冊 Office PIA，才能執行大部分的開發工作。 如需詳細資訊，請參閱 [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。

 使用者電腦不需要 Office PIA 即可執行以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的 Office 方案。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

### <a name="use-types-in-primary-interop-assemblies"></a>在主要 interop 元件中使用類型
 Office PIA 包含會公開 Office 應用程式物件模型的類型組合，以及不打算直接用於程式碼中的其他基礎結構類型。 如需 Office Pia 中的類型總覽，請參閱 [office 主要 interop 元件中的類別和介面總覽](/previous-versions/office/office-12/ms247299\(v\=office.12\))。

 由於 Office PIA 中的類型對應到以 COM 為基礎的物件模型中的類型，您使用這些類型的方式通常與其他 Managed 類型不同。 比方說，您呼叫在 Office 主要 Interop 組件中有選擇性參數之方法的方式，取決於您在專案中所使用的程式設計語言。 如需詳細資訊，請參閱下列主題：

- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)。

- [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)。

## <a name="program-model-of-office-projects"></a>Office 專案的程式模型
 所有的 Office 專案包含一個或多個產生的類別，它們提供您程式碼的進入點。 這些類別也會提供對主應用程式物件模型的存取，以及對執行窗格和自訂工作窗格等功能的存取。

### <a name="understand-the-generated-classes"></a>瞭解產生的類別
 在 Excel 和 Word 的文件層級專案中，產生的類別類似於應用程式物件模型中的最上層物件。 例如，Word 文件專案中產生的 `ThisDocument` 的類別會提供與 Word 物件模型中的 <xref:Microsoft.Office.Interop.Word.Document> 類別相同的成員。 如需檔層級專案中產生之類別的詳細資訊，請參閱 [程式檔層級自訂程式](../vsto/programming-document-level-customizations.md)。

 VSTO 增益集專案提供稱為 `ThisAddIn`的產生類別。 此類別與主應用程式物件模型中的類別不相似。 相反地，這個類別代表 VSTO 增益集本身，並提供可用來存取主應用程式物件模型以及存取 VSTO 增益集可用之其他功能的成員。如需詳細資訊，請參閱 [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。

 Office 專案中所有產生的類別都包括 `Startup` 和 `Shutdown` 事件處理常式。 若要開始撰寫程式碼，您通常將程式碼加入這些事件處理常式。 若要初始化 VSTO 增益集，您可以將程式碼加入 `Startup` 事件處理常式。 若要清除 VSTO 增益集使用的資源，您可以將程式碼加入 `Shutdown` 事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

### <a name="access-the-generated-classes-at-run-time"></a>在執行時間存取產生的類別
 Office 方案載入時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會具現化專案中的每個產生的類別。 您可以使用 `Globals` 類別，從專案中的任何程式碼存取這些物件。 例如，您可以使用類別， `Globals` `ThisAddIn` 從 VSTO 增益集中的功能區按鈕的事件處理常式呼叫類別中的程式碼。

 如需詳細資訊，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。

### <a name="namespace-considerations-in-office-solutions"></a>Office 方案中的命名空間考慮
 建立專案之後，您無法變更 Office 專案的 *「預設命名空間」* (default namespace) (或 Visual Basic 中的 *「根命名空間」* (root namespace))。 預設命名空間會永遠符合您在建立專案時指定的專案名稱。 如果您重新命名您的專案，不會變更預設命名空間。 如需專案中預設命名空間的詳細資訊，請參閱專案設計工具 [、專案設計工具 &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) 和 [應用程式頁面、專案設計工具 &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md)。

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>在 c # 專案中變更主專案類別的命名空間
 主項目類別 (例如 `ThisAddIn`、 `ThisWorkbook`或 `ThisDocument` 類別) 在 Visual C# Office 專案中有自己的命名空間。 根據預設，專案中主項目的命名空間會符合您在建立專案時指定的專案名稱。

 若要變更 Visual C# Office 專案中的主項目命名空間，請使用 [主項目命名空間]  屬性。 如需詳細資訊，請參閱 [Office 專案中的屬性](../vsto/properties-in-office-projects.md)。

## <a name="supported-programming-languages-in-office-projects"></a>Office 專案中支援的程式設計語言
 Visual Studio 中的 Office 專案範本只支援 Visual Basic 和 Visual C# 程式設計語言。 因此，這些專案範本只位於 **中，[新增專案]****對話方塊的 [Visual Basic]****和 [Visual C#]**[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]節點。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

## <a name="language-choice-and-office-programming"></a>語言選擇和 Office 程式設計
 Microsoft Office 和 Visual Basic for Applications (VBA) 是開發來協同運作以最佳化應用程式自訂的工作流程。 Visual Basic 繼承了一些開發。 例如，Visual Basic 支援選擇性參數，這表示在呼叫 Microsoft Office 主要 Interop 組件中的一些方法時，您可以比使用 Visual C# 撰寫較少程式碼。

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>在 Office 方案中使用 Visual Basic 與 Visual c # 的程式
 您可以使用 Visual Basic 或 Visual C# 來建立 Office 方案。 由於 Microsoft Office 物件模型的設計是要搭配 Microsoft Visual Basic for Applications (VBA) 使用，因此 Visual Basic 開發人員可以輕鬆使用 Microsoft Office 應用程式所公開的物件。 Visual C# 開發人員可以與 Visual Basic 開發人員使用大部分相同的功能，但有某些情況下，他們必須撰寫額外程式碼以使用 Office 物件模型。 Office 程式開發中的基本程式設計功能與以 Visual Basic 和 C# 撰寫的 Managed 程式碼之間也有一些差異。

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Visual Basic 與 Visual C 之間的主要差異#
<!-- markdownlint-enable MD003 MD020 -->

下表顯示 Office 程式開發中的 Visual Basic 和 Visual C# 之間的主要差異。

|功能|描述|Visual Basic 支援|Visual C# 支援|
|-------------|-----------------|--------------------------|------------------------|
|選擇性參數|許多 Microsoft Office 方法有在您呼叫方法時非必要的參數。 如果針對參數不傳遞任何值，會使用預設值。|Visual Basic 支援選擇性參數。|Visual C# 在大部分情況下支援選擇性參數。 如需詳細資訊，請參閱 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)。|
|以傳址方式傳遞參數|大部分的 Microsoft Office 主要 Interop 組件中的選擇性參數可以傳值方式傳遞。 不過，在某些主要 Interop 組件中，接受參考類型的選擇性參數必須以傳址方式傳遞。<br /><br /> 如需有關值和參考型別參數的詳細資訊，請參閱以 [傳值方式傳遞引數，並以傳址方式 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic [C) 程式設計手冊 &#40;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。|以傳址方式傳遞參數不需要額外工作。 Visual Basic 編譯器會在必要時自動以傳址方式傳遞這些參數。|在大部分情況下，Visual C# 編譯器會在必要時自動以傳址方式傳遞這些參數。 如需詳細資訊，請參閱 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)。|
|參數化屬性|某些屬性接受參數，並做為唯讀的函式。|Visual Basic 支援接受參數的屬性。|Visual C# 支援接受參數的屬性。|
|晚期繫結|晚期繫結牽涉到在執行階段判斷物件的屬性，而不是在設計階段將變數轉型為物件類型。|Visual Basic 會在 **Option Strict** 關閉時執行晚期繫結。 當 **Option Strict** 開啟時，您必須明確轉換物件並在 <xref:System.Reflection> 命名空間中使用類型來存取晚期繫結成員。 如需詳細資訊，請參閱 [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)。|Visual C# 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標的專案中執行晚期繫結。 如需詳細資訊，請參閱 [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)。|

## <a name="key-differences-between-office-development-and-managed-code"></a>Office 程式開發和 managed 程式碼之間的主要差異
 下表顯示 Office 程式開發與以 Visual Basic 或 Visual C# 撰寫的 Managed 程式碼之間的主要差異。

|功能|描述|Visual Basic 和 Visual C# 支援|
|-------------|-----------------|-----------------------------------------|
|陣列索引|Microsoft Office 應用程式中的集合的較低陣列界限從 1 開始。 Visual Basic 和 Visual C# 使用以 0 為基礎的陣列。 如需詳細資訊，請參閱 [陣列 &#40;C&#35; 程式設計指南&#41;](/dotnet/csharp/programming-guide/arrays/index) 和 [Visual Basic 中的陣列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)。|若要存取 Microsoft Office 應用程式物件模型中的集合的第一個項目，請使用索引 1，而不是 0。|

## <a name="see-also"></a>另請參閱

- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 專案中的事件](../vsto/events-in-office-projects.md)
- [如何：透過主要 interop 元件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)
- [Office 方案的共同開發](../vsto/collaborative-development-of-office-solutions.md)
