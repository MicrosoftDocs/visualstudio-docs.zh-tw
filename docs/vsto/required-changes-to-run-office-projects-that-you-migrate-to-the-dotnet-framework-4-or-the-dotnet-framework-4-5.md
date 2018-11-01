---
title: 必要的變更，執行您移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 78a46fbffdbf849ab9f9584b72c520d5aa1d3624
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670789"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>必要的變更，執行您移轉至.NET Framework 4 或.NET Framework 4.5 的 Office 專案
  如果 Office 專案的目標 framework 變更為[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本從.NET Framework 較早版本，您必須執行下列工作，以確保解決方案可以在開發電腦和終端使用者電腦上執行：  
  
- 如果專案是從 Visual Studio 2008 升級，請移除專案中的 <xref:System.Security.SecurityTransparentAttribute>。  
  
- 執行**清除**能夠執行或偵錯的專案，在開發電腦上的 Visual Studio 中的命令。  
  
- 更新專案的 .NET Framework 必要條件。  
  
- 如果在變更目標 Framework 之前已使用 ClickOnce 部署了解決方案，使用者也必須重新安裝解決方案。  
  
  如需這些工作每一項的詳細資訊，請參閱下列對應的章節。  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>從您從 Visual Studio 2008 升級的專案中移除 SecurityTransparent 屬性  
 如果 Office 專案從 Visual Studio 2008 升級，且專案的目標 Framework 隨後變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須從專案中移除 <xref:System.Security.SecurityTransparentAttribute>。 Visual Studio 不會為您自動移除這個屬性。 如果不移除這個屬性，您就會在編譯專案時收到錯誤訊息。  
  
 如需 Visual Studio 可以在其中變更已升級專案的目標 framework 的條件[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，請參閱[升級和移轉 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>移除 SecurityTransparentAttribute  
  
1.  請使用在 Visual Studio 中開啟的專案，開啟 [方案總管] 。  
  
2.  在 [屬性]  節點 (C#) 或 [我的專案]  節點 (Visual Basic) 下，按兩下 AssemblyInfo 程式碼檔，以在程式碼編輯器中加以開啟。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，您必須按一下 [方案總管]  中的 [顯示所有檔案]  按鈕，才能查看 AssemblyInfo 程式碼檔。  
  
3.  找出 <xref:System.Security.SecurityTransparentAttribute>，並將它從檔案移除或加以註解化。  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>執行偵錯或執行專案，在開發電腦上的 [清除] 命令  
 如果 Office 專案建置專案的目標 framework 變更為之前[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本中，您必須執行**清除**命令，並在之後的目標 framework 變更，然後重建專案。 如果不會執行**Clean**命令時，您會收到<xref:System.Runtime.InteropServices.COMException>當您嘗試偵錯或執行目標的專案。  
  
 如需詳細資訊**Clean**命令，請參閱[建置 Office 方案](../vsto/building-office-solutions.md)。  
  
## <a name="update-the-prerequisites-for-deployment"></a>更新部署的必要條件  
 當您將目標重定至 Office project[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更新版本中，您也必須更新中對應的.NET Framework 必要條件**必要條件** 對話方塊。 否則 ClickOnce 部署或 InstallShield 限量版專案會查找並安裝舊版的 .NET Framework。  
  
 如需有關如何更新使用者電腦的部署必要條件的詳細資訊，請參閱[如何： 在執行 Office 方案的終端使用者電腦上安裝必要條件](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>在使用者電腦上重新安裝解決方案  
 如果您使用 ClickOnce 部署以 .NET Framework 3.5 為目標的 Office 解決方案，然後又將專案目標重定為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，則終端使用者必須解除安裝解決方案，並在您重新發行後再重新安裝解決方案。 如果您重新發行重定目標的方案，方案會更新使用者電腦上，使用者會收到<xref:System.Runtime.InteropServices.COMException>當他們執行更新的方案。  
  
## <a name="see-also"></a>另請參閱  
 [移轉至.NET Framework 4 或更新版本的 Office 方案](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  