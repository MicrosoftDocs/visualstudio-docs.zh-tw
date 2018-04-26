---
title: 範例 Excel 延伸模組：ExtensionPackage 類別
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43234161979df9190daddeec168e7a40a14db498
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>範例 Excel 延伸模組：ExtensionPackage 類別
此類別會擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 類別，並提供將測試 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] Worksheet 之自動程式化 UI 測試的進入點。

## <a name="assembly-attribute"></a>Assembly 屬性
 檔案開頭的 assembly 屬性會將組件識別為 UI 測試擴充功能。

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 這個屬性會宣告基底類別名稱、封裝類別名稱，以及自訂擴充封裝類別的完整類別名稱。

## <a name="simple-properties"></a>簡單屬性
 這個類別的屬性提供值，讓自動程式化 UI 測試架構可以識別及描述擴充功能和組件。 如需詳細資訊，請參閱程式碼註解。

## <a name="getservice-method"></a>GetService 方法
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> 方法是單一進入點，讓自動程式化 UI 測試架構可以存取技術管理員、屬性提供者和動作篩選 (如每個物件的基底類別所識別)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
