---
title: 在單元測試中使用 MSTest
description: 深入瞭解 MSTest 架構，它支援 Visual Studio 中的單元測試。 使用這些類別和成員來撰寫單元測試的程式碼。
ms.custom: SEO-VS-2020
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 4eef06bb48730fba9ba1df145857d41323cbfdd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946315"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>在單元測試中使用 MSTest 架構

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) 架構支援 Visual Studio 中的單元測試。 當您撰寫單元測試程式碼時，請使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間中的類別和成員。 在調整從程式碼產生的單元測試時，也可以利用它們。

## <a name="framework-members"></a>架構成員

為了提供更清楚的單元測試架構概觀，本節將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 命名空間的成員整理成相關功能的群組。

> [!NOTE]
> 名稱以 "Attribute" 結尾的屬性項目，無論結尾有沒有 "Attribute" 都可以使用。 例如，下列兩個程式碼範例的運作完全相同︰
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>用於資料驅動型測試的成員

使用下列項目設定資料驅動型單元測試。 如需詳細資訊，請參閱 [建立資料驅動型單元測試](../test/how-to-create-a-data-driven-unit-test.md) ，並 [使用設定檔來定義資料來源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>用來建立呼叫順序的屬性

以下列屬性裝飾的程式碼項目會在您指定的時間呼叫。 如需詳細資訊，請參閱 [單元測試的剖析](/previous-versions/ms182517(v=vs.110))。

### <a name="attributes-for-assemblies"></a>組件的屬性

AssemblyInitialize 和 AssemblyCleanup 會在載入您的組件之後以及卸載您的組件之前呼叫。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>類別的屬性

ClassInitialize 和 ClassCleanup 會在載入您的類別之後以及卸載您的類別之前呼叫。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>測試方法的屬性

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>用來識別測試類別和方法的屬性

每個測試類別必須具有 `TestClass` 屬性，且每個測試方法必須具有 `TestMethod` 屬性。 如需詳細資訊，請參閱 [單元測試的剖析](/previous-versions/ms182517(v=vs.110))。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert 類別和相關的例外狀況

單元測試可以依照其使用各種判斷提示、例外狀況及屬性的方式，確認特定的應用程式行為。 如需詳細資訊，請參閱 [使用 assert 類別](../test/using-the-assert-classes.md)。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>TestContext 類別

下列屬性和指派給它們的值會顯示在特定測試方法的 Visual Studio [屬性] 視窗中。 這些屬性並不應該透過單元測試的程式碼存取。 相反地，無論是由您透過 Visual Studio 的 IDE，或是由 Visual Studio 測試引擎，它們都會影響單元測試使用或執行的方式。 例如，其中一些屬性會顯示為 [測試管理員] 視窗和 [測試結果] 視窗中的資料行，這表示您可以使用它們來群組或排序測試和測試結果。 這類屬性其中之一為 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>，您可以利用它來將任意中繼資料加入至單元測試。 例如，您可以使用它來儲存此測試所涵蓋之測試進行的名稱，方法是以 `[TestProperty("TestPass", "Accessibility")]` 標示單元測試。 或者，您可以使用它，以 `[TestProperty("TestKind", "Localization")]` 來儲存指出測試為哪種類型的指標。 您使用此屬性建立的屬性，以及您指派的屬性值，都會顯示在 Visual Studio [屬性] 視窗的 [測試專屬] 標題下。

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

## <a name="attributes-used-to-generate-reports"></a>用來產生報表的屬性

本節中的屬性將它們所裝飾的測試方法與 Team Foundation Server 團隊專案的專案階層架構中的實體產生關聯。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>與私用存取子搭配使用的類別

您可以為私用方法產生單元測試。 這個層代會建立私用存取子類別，該類別會具現化 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> 類別的物件。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> 類別是一種包裝函式類別，會使用反映做為私用存取子程序的一部分。 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> 類別很類似，不過是用來呼叫私用靜態方法，而不是呼叫私用執行個體方法。

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 參考文件