---
title: 使用 ServerDocument 類別管理伺服器上的檔
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 739946fc7fc6ea7014fb93010ca85094a7fc7056
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251925"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>使用 ServerDocument 類別管理伺服器上的檔
  您可以使用[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]中`ServerDocument`的類別來管理檔層級自訂的數個層面，即使未安裝 Microsoft Office Word 和 Microsoft Office Excel 也一樣。 您可以執行下列工作：

- 存取和修改檔或活頁簿之資料快取中的資料。 如需詳細資訊，請參閱[使用檔中](#CachedData)的快取資料。

- 管理與檔相關聯的自訂群組件。 如需詳細資訊，請參閱[管理檔自訂](#CustomizationInfo)。

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>瞭解 ServerDocument 類別
 `ServerDocument`類別是設計用來在未安裝 Office 的電腦上使用。 因此，您通常會在不與 Office 整合的應用程式（例如，主控台專案或 Windows Forms 專案，而不是 Office 專案）中使用這個類別。 請使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> *VisualStudio. ServerDocument .dll*元件中的類別。

 類別可以用來操作使用[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]所建立的檔層級自訂。 `ServerDocument`

 如需適用于 Office Runtime 的 Visual Studio 2010 工具和 .NET Framework 的 Office 擴充功能的詳細資訊，請參閱[Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

> [!NOTE]
> 如果您的繼承應用程式使用`ServerDocument` `Visual Studio Tools for Office`系統（版本3.0 執行時間）中的類別，則`Visual Studio Tools for Office`必須在執行應用程式的電腦上安裝系統（版本3.0 執行時間）。 `Visual Studio 2010 Tools for Office runtime`無法執行這些應用程式。

## <a name="CachedData"></a>使用檔中的快取資料
 `ServerDocument`類別會提供您可以用來在自訂檔中處理資料快取的成員。 如需快取資料的詳細資訊，請參閱在伺服器上快取[資料](../vsto/caching-data.md)並[存取檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。

 下表列出您可以用來處理快取資料的成員。

|工作|要使用的成員|
|----------|-------------------|
|判斷檔是否有資料快取。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法|
|存取檔中的快取資料。<br /><br /> 如需詳細資訊，請參閱在[伺服器上存取檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性。|

## <a name="CustomizationInfo"></a>管理檔自訂
 您可以使用`ServerDocument`類別的成員來管理與檔相關聯的自訂群組件。 例如，您可以透過程式設計方式從檔中移除自訂，讓檔不再屬於自訂的一部分。

 下表列出您可以用來管理自訂群組件的成員。

|工作|要使用的成員|
|----------|-------------------|
|判斷檔是否為檔層級自訂的一部分。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法|
|以程式設計方式，在執行時間將自訂附加至檔。<br /><br /> 如需詳細資訊，請參閱[如何：將 managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|其中一個方法<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 。|
|以程式設計方式在執行時間從檔中移除自訂。<br /><br /> 如需詳細資訊，請參閱[如何：從檔](../vsto/how-to-remove-managed-code-extensions-from-documents.md)移除 Managed 程式碼擴充。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法|
|取得與檔相關聯之部署資訊清單的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 屬性。|

## <a name="see-also"></a>另請參閱
- [如何：將 managed 程式碼擴充附加至檔](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [如何：從檔移除 managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [快取資料](../vsto/caching-data.md)
