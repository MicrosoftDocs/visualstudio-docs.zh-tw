---
title: 擴充自動程式化 UI 測試和動作記錄
description: 瞭解如何利用自動程式化 UI 測試架構的擴充性，為特定的 UI 建立自動程式化 UI 測試架構的擴充功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6a2996da30c0be8e3dc4d303d0e46e901c8b885d
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442621"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>擴充自動程式化 UI 測試和動作記錄

自動程式化 UI 測試的測試架構和動作記錄並不支援所有可能的使用者介面。 它可能不支援您要測試的特定 UI。 例如，您無法立即為 Microsoft Excel 試算表建立自動程式化 UI 測試或動作記錄。 不過，您可以利用自動程式化 UI 測試架構的擴充性，建立您自己的自動程式化 UI 測試架構延伸模組來支援特定 UI。

![UI 測試架構](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>測試 Microsoft Excel 的範例延伸模組

此[部落格文章](/archive/blogs/gautamg/3-introducing-sample-excel-extension)包含自動程式化 UI 測試架構的[範例延伸模組](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip)連結。 您也可以檢視[自動程式化 UI 測試擴充性的整個部落格文章系列](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility)。

> [!NOTE]
> 此範例主要搭配 Microsoft Excel 2010 使用。 不一定適用於 Excel 的其他版本。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [自動程式碼 UI 測試的最佳作法](../test/best-practices-for-coded-ui-tests.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)