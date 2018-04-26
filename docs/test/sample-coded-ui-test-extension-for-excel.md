---
title: Excel 的範例自動程式碼 UI 測試擴充功能
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2c76ba569a6f9f34d28d6aaaa268a366c1be7b31
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Excel 的範例自動程式碼 UI 測試擴充功能
範例的擴充元件執行於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 自動程式化 UI 測試處理序，具有一些階層性，並以 `ExtensionPackage` 類別為基底。 `TechnologyManager`、`ActionFilter` 和 `PropertyProvider` 類別位於下一個層級，控制項項目位於最上層。

 ![Excel 測試延伸模組架構](../test/media/excel_extarch.png "Excel_ExtArch") Excel 測試延伸模組架構

## <a name="extension-points"></a>擴充點
 這些類別代表範例中啟用 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 自動程式化 UI 測試所實作的擴充點。

### <a name="extensionpackage"></a>ExtensionPackage
 繼承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 類別，這是自動程式化 UI 測試延伸模組的進入點。 實作這個抽象類別，可允許自動程式化 UI 測試架構對自訂 UI 測試技術管理員、UI 測試屬性提供者和 UI 測試動作篩選條件的內部存取，以測試新 UI。 如需詳細資訊，請參閱 [ExtensionPackage 類別](../test/sample-excel-extension-extensionpackage-class.md)。

### <a name="technologymanager"></a>TechnologyManager
 繼承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 類別，這個類別提供技術管理員進行測試錄製和播放。 如需詳細資訊，請參閱 [TechnologyManager 類別](../test/sample-excel-extension-technologymanager-class.md)。

### <a name="actionfilter"></a>ActionFilter
 繼承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 類別，這個類別提供基底類別，以將類似的測試動作結果彙總至單一測試結果。 如需詳細資訊，請參閱 [ActionFilter 類別](../test/sample-excel-extension-actionfilter-class.md)。

### <a name="technology-elements"></a>技術項目
 繼承自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 類別的基底類別，為 UI 測試中可錄製和播放的技術項目提供基礎。 如需詳細資訊，請參閱 [Element 類別](../test/sample-excel-extension-element-classes.md)。

### <a name="propertyprovider"></a>PropertyProvider
 繼承自 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 類別，這個類別提供基底類別，以支援測試錄製和播放的 UI 項目屬性。 如需詳細資訊，請參閱 [PropertyProvider 類別](../test/sample-excel-extension-propertyprovider-class.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage 類別](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager 類別](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter 類別](../test/sample-excel-extension-actionfilter-class.md)
- [Element Class類別](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider 類別](../test/sample-excel-extension-propertyprovider-class.md)
