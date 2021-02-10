---
title: 遷移至 .NET 4.5 的 Office 專案所需的變更
description: 如果目標 framework 從舊版 .NET Framework 變更為 .NET Framework 4 或更新版本，請瞭解您需要對專案進行的變更。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fbe3c311e734cc076ab898544470c3e27e91795
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943714"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>遷移至 .NET 4.5 的 Office 專案所需的變更

  如果 Office 專案的目標 framework [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 從舊版 .NET Framework 變更為或更新版本，您必須執行下列工作，以確保解決方案可以在開發電腦和終端使用者電腦上執行：

- 如果專案是從 Visual Studio 2008 升級，請移除專案中的 <xref:System.Security.SecurityTransparentAttribute>。

- 在 Visual Studio 中執行 [ **清除** ] 命令，以便能夠在開發電腦上執行或偵測專案。

- 更新專案的 .NET Framework 必要條件。

- 如果在變更目標 Framework 之前已使用 ClickOnce 部署了解決方案，終端使用者也必須重新安裝解決方案。

  如需這些工作每一項的詳細資訊，請參閱下列對應的章節。

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>從 Visual Studio 2008 升級的專案中移除 SecurityTransparent 屬性
 如果 Office 專案從 Visual Studio 2008 升級，且專案的目標 Framework 隨後變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須從專案中移除 <xref:System.Security.SecurityTransparentAttribute>。 Visual Studio 不會為您自動移除這個屬性。 如果不移除這個屬性，您就會在編譯專案時收到錯誤訊息。

 如需 Visual Studio 可以將升級專案的目標 framework 變更為或的條件的詳細資訊 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ，請參閱 [升級和遷移 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。

#### <a name="to-remove-the-securitytransparentattribute"></a>移除 SecurityTransparentAttribute

1. 請使用在 Visual Studio 中開啟的專案，開啟 [方案總管] 。

2. 在 [屬性]  節點 (C#) 或 [我的專案]  節點 (Visual Basic) 下，按兩下 AssemblyInfo 程式碼檔，以在程式碼編輯器中加以開啟。

    > [!NOTE]
    > 在 Visual Basic 專案中，您必須按一下 [方案總管]  中的 [顯示所有檔案]  按鈕，才能查看 AssemblyInfo 程式碼檔。

3. 找出 <xref:System.Security.SecurityTransparentAttribute>，並將它從檔案移除或加上註解。

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>執行 [清除] 命令，以在開發電腦上進行調試或執行專案
 如果 Office 專案是在專案的目標 framework 變更為或更新版本之前建立的 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ，則您必須執行 [ **清除** ] 命令，然後在目標 framework 變更之後重建專案。 如果沒有執行 **乾淨** 的命令， <xref:System.Runtime.InteropServices.COMException> 當您嘗試偵測或執行重定目標的專案時，將會收到。

 如需 **Clean** 命令的詳細資訊，請參閱 [建立 Office 方案](../vsto/building-office-solutions.md)。

## <a name="update-the-prerequisites-for-deployment"></a>更新部署的必要條件
 當您將 Office 專案的目標重定為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本時，您也必須更新 [ **必要條件** ] 對話方塊中對應的 .NET Framework 先決條件。 否則 ClickOnce 部署或 InstallShield 限量版專案會查找並安裝舊版的 .NET Framework。

 如需有關更新部署至使用者電腦之必要條件的詳細資訊，請參閱 [如何：在終端使用者電腦上安裝必要條件以執行 Office 解決方案](/previous-versions/bb608608(v=vs.110))。

## <a name="reinstall-solutions-on-end-user-computers"></a>在終端使用者電腦上重新安裝解決方案
 如果您使用 ClickOnce 部署以 .NET Framework 3.5 為目標的 Office 解決方案，然後又將專案目標重定為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，則使用者必須解除安裝解決方案，並在您重新發行後再重新安裝解決方案。 如果您重新發行重定目標的解決方案，並在終端使用者電腦上更新解決方案，終端使用者會在 <xref:System.Runtime.InteropServices.COMException> 執行更新的解決方案時收到。

## <a name="see-also"></a>另請參閱
- [將 Office 方案遷移至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)