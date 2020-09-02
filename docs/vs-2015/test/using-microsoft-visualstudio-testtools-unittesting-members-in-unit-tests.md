---
title: 在單元測試中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成員 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e8b3ea10b96a63bd18098030dc884ac3f3383353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657191"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>在單元測試中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
單元測試架構支援 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的單元測試。 當您撰寫單元測試程式碼時，請使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間中的類別和成員。 當您從頭開始撰寫單元測試，或正在調整從您正在測試的程式碼所產生的單元測試時，您可以使用它們。

## <a name="groups-of-elements"></a>項目群組
 為了提供更清楚的單元測試架構概觀，本節將 UnitTesting 命名空間的項目整理成相關功能的群組。

> [!NOTE]
> 屬性項目 (名稱以字串屬性結尾)，可以在包含或不包含字串屬性的情況下使用。 例如，下列兩個程式碼範例的運作完全相同︰
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>用於資料驅動型測試的項目
 使用下列項目設定資料驅動型單元測試。 如需詳細資訊，請參閱[如何：建立資料驅動型單元測試](../test/how-to-create-a-data-driven-unit-test.md)和[逐步解說︰使用組態檔定義資料來源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>用來建立呼叫順序的屬性
 以下列屬性裝飾的程式碼項目會在您指定的時間呼叫。 如需詳細資訊，請參閱[單元測試的結構](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)。

### <a name="for-assemblies"></a>針對組件
 AssemblyInitialize 和 AssemblyCleanup 會在載入您的組件之後以及卸載您的組件之前呼叫。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>針對類別
 ClassInitialize 和 ClassCleanup 會在載入您的類別之後以及卸載您的類別之前呼叫。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>針對測試方法

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>用來識別測試類別和方法的屬性
 每個測試類別必須具有 TestClass 屬性，且每個測試方法必須具有 TestMethod 屬性。 如需詳細資訊，請參閱[單元測試的結構](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert 類別和相關的例外狀況
 單元測試可以依照其使用各種 Assert 陳述式、例外狀況及屬性的方式，確認特定的應用程式行為。 如需詳細資訊，請參閱[使用 Assert 類別](../test/using-the-assert-classes.md)。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>TestContext 類別
 下列屬性和指派給它們的值會顯示在特定測試方法的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [屬性] 視窗中。 這些屬性並不應該透過單元測試的程式碼存取。 相反地，它們會影響單元測試的使用或執行方式，無論是透過您或 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的 IDE，或是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 測試引擎。例如，其中一些屬性會顯示為 [測試管理員] 視窗和 [測試結果] 視窗中的資料行，這表示您可以使用它們來群組或排序測試和測試結果。 這類屬性其中之一為 TestPropertyAttribute，您可以利用它來將任意中繼資料加入至單元測試。 例如，您可以使用它來儲存此測試所涵蓋之測試進行的名稱，方法是以 `[TestProperty("TestPass", "Accessibility")]` 標示單元測試。 或者，您可以使用它來儲存指出測試為哪種類型的指標：`[TestProperty("TestKind", "Localization")]`。 您使用此屬性建立的屬性，以及您指派的屬性值，都會顯示在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [屬性] 視窗的 [測試專屬]**** 標題下。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>測試組態類別

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>用於產生報告的屬性
 本節中的屬性將它們所裝飾的測試方法與 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 團隊專案的專案階層架構中的實體產生關聯。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>與私用存取子搭配使用的類別
 如[使用 Publicize 建立私用存取子](https://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb)中所述，您可以產生適用於私用方法的單元測試。 這個層代會建立私用存取子類別，該類別會具現化 PrivateObject 類別的物件。 PrivateObject 類別是一種包裝函式類別，會使用反映做為私用存取子程序的一部分。 PrivateType 類別很類似，不過是用來呼叫私用靜態方法，而不是呼叫私用執行個體方法。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>