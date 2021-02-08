---
title: 升級和遷移 Office 方案
description: 如果您有在舊版 Visual Studio 中建立的 Offince 專案，您必須升級專案，才能在目前版本的 Visual Studio 中使用它。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 61961420167d30247ba3dc33122d6c0e7cad8d45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838317"
---
# <a name="upgrade-and-migrate-office-solutions"></a>升級和遷移 Office 方案
  如果您有使用舊版 Visual Studio 建立的 Microsoft Office 專案，則必須升級專案以便在目前的 Visual Studio 版本中使用。 若要升級 Microsoft Office 專案，請在包含 Microsoft Office 開發人員工具的 Visual Studio 版本中開啟。 如需包含 Microsoft Office 開發人員工具的 Visual Studio 版本的詳細資訊，請參閱 [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)。

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio 無法升級使用舊版 Visual Studio 所建立的 InfoPath 表單範本專案。 目前的 Visual Studio 版本不支援這些類型的專案。

## <a name="changes-to-upgraded-projects"></a>升級專案的變更
 當您升級 Microsoft Office 專案時，Visual Studio 會修改專案以將目標設為下列項目：

- 適用于 Office 執行時間的 Visual Studio 2010 工具。 如需詳細資訊，請參閱 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

- 目前組件的參考。

- 該專案類型支援的 .NET Framework 版本 (唯有升級至 Visual Studio 2013 時)。

- 該專案類型支援的 Microsoft Office 版本 (唯有升級至 Visual Studio 2013 時)。

## <a name="assembly-references"></a>組件參考
 Visual Studio 會升級專案中的下列組件參考：

- Microsoft Office 主要 Interop 組件 (PIA)。

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]中的組件。 如需這些元件的詳細資訊，請參閱 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

- 全新或更新版本的相依組件。

## <a name="targeted-net-framework"></a>目標 .NET Framework
 當專案升級至 Visual Studio 2013 時，Visual Studio 會將專案修改為以 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 或 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標。 該專案所設定的目標 .NET framework 版本，取決於您電腦上安裝的 Office 版本。 如果已安裝 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ，Visual Studio 會將專案修改成以 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]為目標。 否則，Visual Studio 修改專案成以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標。

> [!NOTE]
> 您可能需要執行一些額外的步驟，在開發和使用者電腦上執行重定目標的方案，且如果該專案使用特定的功能，也將無法再對進行編譯。 如需詳細資訊，請參閱將 [Office 方案遷移至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)。

 如果您在 Office 專案中以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標，則可以使用以 .NET Framework 3.5 為目標時無法使用的功能。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

## <a name="targeted-office-application"></a>目標 Office 應用程式
 當 Office 專案升級至 Visual Studio 2013 時，Visual Studio 會將專案修改成以專案類型支援的 Microsoft Office 版本為目標，例如文件層級自訂專案或 VSTO 增益集專案。

 Visual Studio 2013 中的 Office 專案只能以 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 應用程式為目標。 Visual Studio 會將專案的目標修改為目標已安裝的 Office 最新版本。 如未安裝這些版本的 Office，Visual Studio 就不會升級專案。

> [!NOTE]
> 如果您將 VSTO 增益集專案升級至目標 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或更新版本，請確定 `ThisAddIn_Startup` VSTO 增益集的事件處理常式不包含會存取應用程式中檔的程式碼。 如需詳細資訊，請參閱 [Office 應用程式啟動時存取檔](../vsto/programming-vsto-add-ins.md#AccessingDocuments)。

 針對檔層級自訂， [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] 會將具有二進位格式之專案中的檔（例如副檔名為 *.xls* 或副檔名的檔 ）轉換成 Office Open XML 格式。 如需 Open XML 的詳細資訊，請參閱 [新副檔名和 OPEN xml 格式簡介](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1)。

> [!NOTE]
> 智慧標籤在 Excel 2010 和 Word 2010 中已被取代。 因此，如果您的方案使用智慧標籤，必須先將其移除，然後才可於  Visual Studio 2013 或 Visual Studio 2015 中進行測試及偵錯。

## <a name="upgrade-microsoft-office-2003-projects"></a>升級 Microsoft Office 2003 專案
 有一些升級文件層級自訂和 VSTO 增益集 (其以 Microsoft Office 2003 為目標) 的額外考量。

### <a name="document-level-projects"></a>檔層級專案
 如果專案中的文件包含 Windows Form 控制項，則必須在升級專案之前，先安裝 Visual Studio 2005 Tools for Office Second Edition Runtime。 如果升級專案前未於開發電腦上安裝此版本的執行階段，則升級的專案可能會包含編譯或執行階段錯誤。 完成專案升級後，可以解除安裝開發電腦中的 Visual Studio 2005 Tools for Office Second Edition Runtime (如果沒有其他 Office 方案正在使用它)。 您可以從下列 Microsoft 下載中心，取得這個執行階段版本的可轉散發套件： [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392)。

### <a name="vsto-add-in-projects"></a>VSTO 增益集專案
 如果您原始專案的方案檔包含安裝程式或 InstallShield 限量版專案 (已設定為安裝 VSTO 增益集)，則 Visual Studio 會升級專案，但不會進一步變更專案。 如果想要繼續使用 Windows Installer 檔案來部署 VSTO 增益集，則必須將安裝程式或 InstallShield 限量版專案修改成安裝新的必要元件，例如 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、Visual Studio 2010 Tools for Office Runtime，以及 VSTO 增益集所參考的主要 Interop 組件 (選擇性)。 如需詳細資訊，請參閱 [使用 Windows Installer 部署 Office 方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

 如果要使用 ClickOnce 部署 VSTO 增益集，可以整個刪除安裝程式或 InstallShield 限量版專案。 如需使用 ClickOnce 部署 VSTO 增益集的詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [如何：升級 Office 方案](/previous-versions/4bez6837(v=vs.140))
- [將 Office 方案遷移至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [選項對話方塊、專案升級](../vsto/project-upgrade-options-dialog-box.md)