---
title: 使用 ServerDocument 類別管理伺服器上的檔
description: 瞭解如何在 Visual Studio Tools for Office 執行時間中使用 ServerDocument 類別，以管理檔層級自訂的數個層面。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17a25ca382cfbbc762731afacaa628de616cfe1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879471"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>使用 ServerDocument 類別管理伺服器上的檔
  您可以使用 `ServerDocument` 中的類別 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 來管理檔層級自訂的數個層面，即使未安裝 Microsoft Office Word 和 Microsoft Office Excel 也是如此。 您可以執行下列工作：

- 存取和修改檔或活頁簿之資料快取中的資料。 如需詳細資訊，請參閱使用 [檔中](#CachedData)的快取資料。

- 管理與檔相關聯的自訂群組件。 如需詳細資訊，請參閱 [管理檔自訂](#CustomizationInfo)。

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>瞭解 ServerDocument 類別
 `ServerDocument`類別的設計目的是在未安裝 Office 的電腦上使用。 因此，您通常會在未與 Office 整合的應用程式（例如主控台專案或 Windows Forms 專案，而非 Office 專案）中使用此類別。 使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* 元件中的類別。

 `ServerDocument`類別可以用來操作使用建立的檔層級自訂 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 。

 如需適用于 Office 執行時間的 Visual Studio 2010 工具和 .NET Framework 的 Office 擴充功能的詳細資訊，請參閱 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

> [!NOTE]
> 如果您的繼承應用程式使用 `ServerDocument` 系統中的類別 `Visual Studio Tools for Office` (3.0 版執行時間) ，則 `Visual Studio Tools for Office` 必須在執行應用程式的電腦上安裝 system (3.0 版執行時間) 。 `Visual Studio 2010 Tools for Office runtime`無法執行這些應用程式。

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> 使用檔中的快取資料
 `ServerDocument`類別會提供您可用來處理自訂檔中資料快取的成員。 如需快取資料的詳細資訊，請參閱快取 [資料](../vsto/caching-data.md) 和 [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。

 下表列出您可以用來處理快取資料的成員。

|Task|要使用的成員|
|----------|-------------------|
|判斷檔是否有資料快取。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法|
|存取檔中的快取資料。<br /><br /> 如需詳細資訊，請參閱 [存取伺服器檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性。|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> 管理檔自訂
 您可以使用類別的成員 `ServerDocument` 來管理與檔相關聯的自訂群組件。 例如，您可以透過程式設計方式從檔中移除自訂，使檔不再是自訂的一部分。

 下表列出您可用來管理自訂群組件的成員。

|Task|要使用的成員|
|----------|-------------------|
|判斷檔是否為檔層級自訂的一部分。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法|
|以程式設計方式在執行時間將自訂附加至檔。<br /><br /> 如需詳細資訊，請參閱 [如何：將 managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|其中一個 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。|
|以程式設計方式在執行時間從檔中移除自訂。<br /><br /> 如需詳細資訊，請參閱 [如何：從檔移除 managed 程式碼延伸](../vsto/how-to-remove-managed-code-extensions-from-documents.md)模組。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法|
|取得與檔相關聯之部署資訊清單的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 屬性。|

## <a name="see-also"></a>另請參閱
- [如何：將 managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [如何：從檔中移除 managed 程式碼延伸模組](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [快取資料](../vsto/caching-data.md)
