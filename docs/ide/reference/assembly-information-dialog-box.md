---
title: 組件資訊對話方塊
description: 瞭解 [元件資訊] 對話方塊，以及如何使用它來指定 .NET Framework 全域程式集屬性的值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d1ed2fd5fe9e49ab947752f84accb326499392fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836418"
---
# <a name="assembly-information-dialog-box"></a>組件資訊對話方塊

您可以使用 [組件資訊] 對話方塊來指定 .NET Framework 全域組件屬性的值，該值會儲存在隨專案自動建立的 AssemblyInfo 檔案中。 在 [方案總管] 中，AssemblyInfo 檔案位於 Visual Basic 專案的 [我的專案] 節點中 (按一下 [顯示所有檔案] 以檢視它)。 針對 C# 專案，它位於 [屬性] 底下。 如需詳細資訊，請參閱[屬性 (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index)。

若要存取此對話方塊，請在 [方案總管] 中選取專案節點，然後在 [專案] 功能表上，選取 [屬性]。在 [應用程式] 頁面上，選取 [組件資訊] 按鈕。

## <a name="uielement-list"></a>UIElement 清單

**標題**\
指定組件資訊清單的標題。 對應至 <xref:System.Reflection.AssemblyTitleAttribute>。

**說明**\
指定組件資訊清單的選擇性描述。 對應至 <xref:System.Reflection.AssemblyDescriptionAttribute>。

**公司**\
指定組件資訊清單的公司名稱。 對應至 <xref:System.Reflection.AssemblyCompanyAttribute>。

您可以在登錄中設定或變更 [公司] 的預設值。 視您的 Windows 版本而定，請在 **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** 或 **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** 索引鍵下尋找 **RegisteredOrganization** 值。

**產品**\
指定組件資訊清單的產品名稱。 對應至 <xref:System.Reflection.AssemblyProductAttribute>。

**版權**\
指定組件資訊清單的著作權標示。 對應至 <xref:System.Reflection.AssemblyCopyrightAttribute>。

**商標**\
指定組件資訊清單的商標。 對應至 <xref:System.Reflection.AssemblyTrademarkAttribute>。

**元件版本**\
指定組件的版本。 對應至 <xref:System.Reflection.AssemblyVersionAttribute>。

**檔案版本**\
指示版本號碼，以指示編譯器使用 Win32 檔案版本資源的特定版本。 對應至 <xref:System.Reflection.AssemblyFileVersionAttribute>。

**Guid**\
識別組件的唯一 GUID。 當您建立專案時，Visual Studio 會產生組件的 GUID。 對應至 <xref:System.Guid>。

**中性語言**\
指定組件所支援的文化特性。 對應至 <xref:System.Resources.NeutralResourcesLanguageAttribute>。 預設值為 [ **無] ()**。

**使元件變成 COM 可見**\
指定組件中的類型是否可供 COM 使用。 對應至 <xref:System.Runtime.InteropServices.ComVisibleAttribute>。

> [!NOTE]
> 如需在 .NET Framework 類別庫中產生 NuGet 套件時設定這些屬性的詳細資訊，請參閱設定 [封裝的專案屬性](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package)。

## <a name="see-also"></a>另請參閱

- [Application Page, Project Designer (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [屬性](/previous-versions/z0w1kczw(v=vs.140))