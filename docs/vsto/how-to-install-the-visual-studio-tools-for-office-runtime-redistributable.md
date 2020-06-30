---
title: 如何：安裝 Visual Studio Tools for Office 執行時間可轉散發套件
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef71de75be5977ab80cbdd85448daa5de381c077
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547221"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>如何：安裝 Visual Studio Tools for Office 執行時間可轉散發套件
  您必須在執行使用 Microsoft Office 開發人員工具所建立之解決方案的每部電腦上，安裝適用于 Office runtime 的 Visual Studio 2010 工具 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 當您安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 Microsoft Office 時，此執行階段會自動安裝。 如需詳細資訊，請參閱[Visual Studio Tools for Office 執行時間安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。

[!include[Add-ins note](includes/addinsnote.md)]

 在下列情況下，您可能需要遵循手動安裝指示：

- 您需要在伺服器上安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 例如，您想要使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別管理伺服器上的文件層級方案。

- 您需要在已安裝所有其他 Office 方案必要條件的電腦上安裝執行階段。

    > [!NOTE]
    > 您必須是開發電腦上的系統管理員，才能安裝 .NET Framework 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>安裝 Visual Studio Tools for Office Runtime

1. 請安裝 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本。

    - 若要下載 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，請參閱[Microsoft .NET Framework 4 （Web 安裝程式）](https://www.microsoft.com/download/details.aspx?id=17851)。

    - 若要下載 [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] ，請參閱[Microsoft .NET Framework 4 用戶端設定檔（Web 安裝程式）](https://www.microsoft.com/download/details.aspx?id=17113)。

    - 若要下載 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ，請參閱[Microsoft .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653)。

2. 執行*vstor_redist.exe*以安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。

     您可以從[適用于 Office runtime 的 Visual Studio 2010 工具](https://www.microsoft.com/download/details.aspx?id=56961)下載這些安裝檔。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的必要條件符合 .NET Framework 的必要條件。

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 包含語言套件。 如果您的 Windows 安裝設定為英文以外的語言，您可以使用在 Windows 上的相同語言顯示執行階段訊息。 同樣地，如果終端使用者安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，然後在安裝設定為英文以外之語言的 Windows 上執行您的方案，則執行階段訊息會以和 Windows 使用的相同語言顯示。 在某些情況下，您可能需要額外的語言套件。 例如，如果您的 Windows 複本使用多個語言設定，或在安裝後切換至另一種語言，則您可能需要其他語言套件 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 您可以在[適用于 Microsoft Office 系統（版本4.0 執行時間）語言套件的 Microsoft Visual Studio 2010 工具](https://www.microsoft.com/download/details.aspx?id=54246)中找到語言套件。

## <a name="see-also"></a>另請參閱
- [在 Visual Studio&#41;中 &#40;Office 開發入門](../vsto/getting-started-office-development-in-visual-studio.md)
- [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [如何：設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [如何：安裝 Office 主要 interop 元件](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [使用 ServerDocument 類別管理伺服器上的檔](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
