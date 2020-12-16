---
title: 透過主要 interop 元件以 Office 應用程式為目標
description: 瞭解如何使用 Visual Studio 透過主要 interop 元件以程式設計的方式將 Microsoft Office 應用程式設為目標。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81c2852a92124a7cf9fb6078b196982d22100be7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528105"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>如何：透過主要 interop 元件以 Office 應用程式為目標
  當您建立新的 Office 專案時，Visual Studio 會自動將參考加入建置專案所需的 Microsoft Office 主要 Interop 組件 (PIA)。 在下列情節中，您必須將參考加入其他 PIA：

- 您想使用專案中其他 Microsoft Office 應用程式的功能。 例如，您想將專案中的 Microsoft Office Excel 功能用於 Microsoft Office Word。

- 您想在 Visual Studio 中自動化沒有專用專案的 Microsoft Office 應用程式 (例如 Microsoft Office Access)。

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>加入主要 Interop 組件的參考

1. 開啟您的 Office 專案，然後在 **方案總管** 中選取專案名稱。

2. 在 [專案] 功能表上，按一下 [加入參考]。

3. 在 [ **架構** ] 索引標籤的 [ **元件名稱** ] 清單中，選取您要的 PIA。 如需有關可用 Microsoft Office 主要 interop 元件的詳細資訊，請參閱 [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)。

     如果專案 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以或更新版本為目標，則預設會將元件參考的 [ **內嵌 Interop 類型** ] 屬性設定為 [ **True** ]。 藉由使用這個項目，方案就不要求使用者電腦上須有 PIA。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

    > [!NOTE]
    > 在 Office 專案中，一律使用 [**加入參考**] 對話方塊的 [ **.net** ] 索引標籤，而不是 [ **COM** ] 索引標籤，以新增 office pia 的參考。如需詳細資訊，請參閱 [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)。

4. 按一下 [確定]。

     元件名稱會出現在 **方案總管** 的 [**參考**] 資料夾中。

## <a name="see-also"></a>另請參閱
- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)
- [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [如何：安裝 Office 主要 interop 元件](../vsto/how-to-install-office-primary-interop-assemblies.md)
